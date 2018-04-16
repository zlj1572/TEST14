# Test3  --使用Intent隐式启动

    Intent也可称为一个在不同组件之间传递的消息，这个消息在到达接收组件后，接收组件会执行相关的动作
    与显式启动不同的是：
      显示启动直接创建对象跳转指定Activity对象，如：
          Intent intent = new Intent(MainActivity.this, SecondActivity.class); 
          startActivity(intent);
      隐式启动则是， Android系统根据Intent的动作和数据来决定启动哪一个Activity。
      也就是说在隐式启动时，Intent中只包含需要执行的动作和所包含的数据,而无需指明具体启动哪一个Activity，选择权有Android系统和最终用户来决定
          如：<activity
                  android:name=".AnotherActivity"            
                  android:label="@string/title_activity_another" >
                  <intent-filter>
                      <action android:name=“startAnotherActivity"/>          -----手动加粗               
                      <category android:name="android.intent.category.DEFAULT"/>
                  </intent-filter>
               </activity>
               
               Intent intent=new Intent();
               intent.setAction("startAnotherActivity");    -----手动加粗
               startActivity(intent);
           这是最简单的页面跳转，但一般视觉看不出来与显式启动的区别。
           隐式启动还可以这样：
           ---打开特定网页
              Intent intent= new Intent(Intent.ACTION_VIEW);        //Action属性
              intent.setData(Uri.parse("http://www.baidu.com"));    //Data属性
              startActivity(intent);
              
              <activity android:name=".Internet">
                  <intent-filter>
                      <action android:name="startWord" />
                      <category android:name="android.intent.category.DEFAULT" />
                      <data android:scheme="http" />   <!-- 响应所有http协议的Internet-->
                  </intent-filter>
               </activity>
               
            ---拨打电话
                Intent intent= new Intent(Intent.ACTION_DIAL);
                intent.setData(Uri.parse("tel:10086"));
                startActivity(intent);
                
                
         关于隐式启动还有很多的组合功能能实现：有兴趣或者有需求的盆友们可以搜索常见的Action，Data组合情况等等。
         
