# Android-basic
Basic elements
线性布局LinearLayout
常用属性：
android:id //标识id		android:layout_width //宽度  		android:layout_height  //高度		android:background //背景

android：layout_margin	//外边距		android:layout_padding	//内边距		android:orientation      //排列格式“水平居中等等”


相对布局RelativeLayout
常用属性:
android:layout_toLeftOf	//在谁的左边		android:layout_toRightOf	//在谁的右边	android:layout_alignBottom   //跟谁底部对齐	android:layout_alignParentBottom  //跟父空间底部对齐
android:layout_below	//在谁的下面

————————————————————————————————————————————

										TextView

文字大小、颜色：
<Button
 android:layout_width="match_parent"
 android:layout_width="match_parent"
 android:layout_height="40dp"
 android:id="@+id/btu_1"	
 android:text="按钮1"
 android:textSize="20sp"	
 android:textColor="#ffffff"
 android:background="#ff9900"/>


自定义背景现状：
name：shape  后缀为xml的文件代码为：
<?xml version="1.0" encoding="utf-8"?>	
<shape xmlns:android="http://schemas.android.com/apk/res/android"
android:shape="rectangle">
<stroke		//边框宽度
android:width="1dp"
android:color="#ff9900"/>	

————————————————————————————————————————————
Button


自定义按压效果：											
在res/drawable文件下创建一个名为bg_btn3的	在res/drawable文件下创建一个名为bg_btn4的					
name：shape  后缀为xml的文件代码为：		
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
<item android:state_pressed="true">		//点击后的颜色
<shape>
<solid android:color="#ff9900"/>
<corners android:radius="5dp"/>
</shape>
<corners		//边角形状						</item>
android:radius="20dp"/>							<item android:state_pressed="false">		//未点击的颜色
</shape>	
							
<shape>
<solid android:color="#aa6600"/>
<corners android:radius="5dp"/>
</shape>
</item>
</selector> 
//构建布局下调用bg_btn4
<Button													      	android:layout_width="match_parent"															android:layout_height="wrap_content"
android:id="@+id/btu_4"
android:text="按钮4"
android:textSize="20sp"
android:textColor="#ffff"
android:layout_below="@id/btu_3"
android:layout_marginTop="10dp"
android:background="@drawable/bg_btn4"
android:onClick="showToast"/>


点击事件：
public class ButtonActivity extends AppCompatActivity {
    private Button mBtn3;	//定义布局里的Button
    private TextView mTv1;	//定义布局里的TextView
    @Nullable
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_button);
        mBtn3=(Button) findViewById(R.id.btu_3);			//调用布局里id为btu_3的Button按钮
        mBtn3.setOnClickListener(new View.OnClickListener() {	//set	onClick事件
            @Override
            public void onClick(View view) {		
                Toast.makeText(ButtonActivity.this,"btn3被点击了",Toast.LENGTH_SHORT).show();
            }
        });
        mTv1=(TextView)findViewById(R.id.tv_1);			//调用布局里id为tv_1的TextView文本
        mTv1.setOnClickListener(new View.OnClickListener() {	//set	onClick事件
            @Override
            public void onClick(View view) {
                Toast.makeText(ButtonActivity.this,"tv1被点击了",Toast.LENGTH_SHORT).show();
            }
        });
    }
    public void showToast(View view){
        Toast.makeText(this,"btn4我被点击了",Toast.LENGTH_SHORT).show();
    }
}

————————————————————————————————————————————

EditText

常用属性：																																			
<EditText																
  android:id="@+id/et_1"		
  android:layout_width="match_parent"													
  android:layout_height="80dp"														
  android:background="@drawable/bg_username"		//引用bg_username.xml的属性包括(边框及其形状，颜色)    					
  android:drawableLeft="@drawable/user"			//导入图片  									
  android:hint="用户名:"					//EditText的hint名 								
  android:inputType="number"				//输入类型规定 									
  android:inputType="number"				//输入类型规定  									
  android:paddingRight="10dp"				//正确边距	
  android:textColor="#ffad33"				//字体颜色	 									
  android:textSize="20sp"					//字体大小     								
  android:maxLines="1"					//输入只有1行        								
  android:layout_marginTop="50dp"/>				//上下间隔	




监听事件：
EditTextActivity.java下操作
public class EditTextActivity extends AppCompatActivity {
private Button mBtnLogin;		//按钮
private EditText mEtUserName;	//EditText（编辑文本）
@Override
protected void onCreate(Bundle savedInstanceState) {
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_edit_text);
//按钮
mBtnLogin=(Button)findViewById(R.id.btn_login);
mBtnLogin.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View view) {										Toast.makeText(EditTextActivity.this,"登录成功",Toast.LENGTH_SHORT).show();
  }
});
																
 mEtUserName=(EditText)findViewById(R.id.et_1);							 mEtUserName.addTextChangedListener(new TextWatcher() {            																@Override        
//在文本之前改变
public void beforeTextChanged(CharSequence charSequence, int i, int i1, int i2) {
    

 }

 @Override
//在文本改变当中
public void onTextChanged(CharSequence charSequence, int i, int i1, int i2) {										 Log.d("edittext",charSequence.toString());
 }	
			
 @Override
 //在文本之后改变
public void afterTextChanged(Editable editable) {           																	 

 }
});   																
 }																
}
     		


制作登录页面：
new->Activity->name->EditTextActivity&&  .xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp">

    <EditText
        android:id="@+id/et_1"
        android:layout_width="match_parent"
        android:layout_height="80dp"
        android:background="@drawable/bg_username"
        android:drawableLeft="@drawable/user"
        android:hint="用户名:"
        android:inputType="number"
        android:paddingLeft="10dp"
        android:paddingRight="10dp"
        android:textColor="#ffad33"
        android:textSize="20sp"
        android:drawablePadding="5dp"
        android:maxLines="1"
        android:layout_marginTop="50dp"/>

    <EditText
        android:layout_width="match_parent"
        android:layout_height="80dp"
        android:id="@+id/et_2"
        android:textSize="20sp"
        android:textColor="#000000"
        android:hint="密码:"
        android:layout_below="@id/et_1"
        android:layout_marginTop="15dp"
        android:inputType="textPassword"
        android:background="@drawable/bg_username"
        android:paddingRight="10dp"
        android:paddingLeft="10dp"
        android:drawableLeft="@drawable/password"
        android:drawablePadding="5dp"
        android:maxLines="1" />

    <Button
        android:layout_width="match_parent"
        android:layout_height="40dp"
        android:id="@+id/btn_login"
        android:layout_below="@id/et_2"
        android:layout_marginTop="40dp"
        android:text="登录"
        android:textSize="20dp"
        android:textColor="#ffffff"
        android:background="@drawable/bg_btn4"/>
</RelativeLayout>			


————————————————————————————————————————————

RadioButton

常用属性：<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp">

    <RadioGroup
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/rg_1"
        android:orientation="vertical">	//设置方向（水平......）

        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/rb_1"
            android:text="男"
            android:textSize="18sp"
            android:textColor="#ff6600"
            android:checked="true"		//默认为男，务必设置id
            android:button="@null"/>	//把按钮去掉
	
        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/rb_2"
            android:text="女"
            android:textSize="18sp"
            android:textColor="#ff6600"/>
    </RadioGroup>

</RelativeLayout>


自定义样式：
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp">

    <RadioGroup
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/rg_1"
        android:orientation="vertical">

        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/rb_1"
            android:text="男"
            android:textSize="18sp"
            android:textColor="#000000"
            android:checked="true"/>

        <RadioButton
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/rb_2"
            android:text="女"
            android:textSize="18sp"
            android:textColor="#000000"/>
    </RadioGroup>

   <RadioGroup
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:id="@+id/rg_2"
       android:orientation="horizontal"
       android:layout_below="@id/rg_1"
       android:layout_marginTop="50dp">

       <RadioButton
           android:layout_width="60dp"
           android:layout_height="30dp"
           android:id="@+id/rb_3"
           android:text="男"
           android:textSize="18sp"
           android:textColor="#000000"
           android:button="@null"
           android:gravity="center"
           android:background="@drawable/radio"/>		//样式引用

       <RadioButton
           android:layout_width="60dp"
           android:layout_height="30dp"
           android:id="@+id/rb_4"
           android:text="女"
           android:textSize="18sp"
           android:textColor="#000000"
           android:button="@null"
           android:gravity="center"
           android:background="@drawable/radio"/>
   </RadioGroup>


//radio.xml文件：

<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_checked="true">
        <shape>
            <solid android:color="#ff9900"/>
            <corners android:radius="5dp"/>
        </shape>
    </item>
    <item android:state_checked="false">
        <shape>
            <stroke android:width="5dp"
                android:color="#aa6600"/>
            <corners android:radius="5dp"/>
        </shape>
    </item>
</selector>

监听事件：

package com.example.androidon;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;

public class RadioButtonActivity extends AppCompatActivity {

    private RadioGroup mRg1;
    private RadioGroup mRg2;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_radio_button);
        mRg1 = (RadioGroup) findViewById(R.id.rg_1);
        mRg1.setOnCheckedChangeListener(new RadioGroup.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup radioGroup, int i) {
                RadioButton radiobutton = (RadioButton) radioGroup.findViewById(i);
                Toast.makeText(RadioButtonActivity.this, radiobutton.getText(), Toast.LENGTH_SHORT).show();
            }
        });
    }
}			


复选框CheckBox
常用属性：
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="15dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="你会那些移动开发！"
        android:textSize="20sp"
        android:textColor="#000"
        android:id="@+id/tv_title" />
    <CheckBox
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Android"
        android:textSize="20dp"
        android:layout_below="@id/tv_title"
        android:id="@+id/cb_1"
        android:button="@drawable/bg_checkbox" />		//图片导入

    <CheckBox
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/cb_2"
        android:text="iOS"
        android:textSize="20sp"
        android:layout_below="@id/cb_1"
        android:button="@drawable/bg_checkbox"/>		//图片导入

    <CheckBox
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/cb_3"
        android:text="H5"
        android:textSize="20sp"
        android:layout_below="@id/cb_2"
        android:button="@drawable/bg_checkbox"/>		//图片导入

    <CheckBox
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:id="@+id/cb_4"
        android:text="其他"
        android:textSize="20sp"
        android:layout_below="@id/cb_3"
        android:button="@drawable/bg_checkbox"/>		//图片导入

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="vertical"
        android:layout_below="@id/cb_4"
        android:layout_marginTop="20dp">
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="你的兴趣："
            android:textSize="20sp"
            android:textColor="#000" />

        <CheckBox
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="编程"
            android:button="@drawable/bg_checkbox"		//图片导入
            android:textSize="20sp"
            android:textColor="#000"
            android:id="@+id/cb_5"/>

        <CheckBox
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/cb_6"
            android:text="睡觉"
            android:textSize="20sp"
            android:textColor="#000"
            android:button="@drawable/bg_checkbox"/>		//图片导入

        <CheckBox
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:id="@+id/cb_7"
            android:text="做饭"
            android:textColor="#000"
            android:textSize="20sp"
            android:button="@drawable/bg_checkbox"/>		//图片导入
    </LinearLayout>
自定义样式：
res下
在draweble包下创建一个.xml样式
<?xml version="1.0" encoding="utf-8"?>
<selector xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:state_checked="false" android:drawable="@drawable/check"/>
    <item android:state_checked="true"  android:drawable="@drawable/check_filled"/>
</selector>



android:button="@drawable/bg_checkbox"/>


监听事件：
在CheckBoxActivity.java下完成监听事件

package com.example.androidon;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.CheckBox;
import android.widget.CompoundButton;
import android.widget.Toast;

public class CheckBoxActivity extends AppCompatActivity {
    private CheckBox mCb6,mCb7;     //声明控件
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_check_box);
        mCb6=(CheckBox) findViewById(R.id.cb_6);
        mCb7=(CheckBox) findViewById(R.id.cb_7);

        mCb6.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton compoundButton, boolean b) {
                Toast.makeText(CheckBoxActivity.this,b?"6选中":"6未选中",Toast.LENGTH_SHORT).show();
            }
        });

        mCb7.setOnCheckedChangeListener(new CompoundButton.OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(CompoundButton compoundButton, boolean b) {
                Toast.makeText(CheckBoxActivity.this,b?"7选中":"7未选择",Toast.LENGTH_SHORT).show();
            }
        });
    }
}		

————————————————————————————————————————————
