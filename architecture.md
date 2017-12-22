Room 和生命周期管理（Lifecycles）的架构组建库 1.0 稳定版正式发布
地址：https://mp.weixin.qq.com/s?__biz=MzAwODY4OTk2Mg==&mid=2652045083&idx=1&sn=3bd46870ded8e1c60bae88c0b3e52141&chksm=808d5f5eb7fad64840e415a4ca1049edfbfcdedae042e9360cdfd5c08525ef85ea222dc50189&mpshare=1&scene=23&srcid=1127DuYHlPR2nD9dxL3YJmMs#rd

使用说明：

1 Lifecycles
1、Adding Components to your Project
Add the Google Maven repository
To add it to your project, open the build.gradle file for your project (not the ones for your app or module) and add the highlighted line as shown below:
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
    }
}


2、Open the build.gradle file for your app or module and add the artifacts that you need as dependencies:

//For Lifecycles, add:
implementation "android.arch.lifecycle:runtime:1.0.3"
annotationProcessor "android.arch.lifecycle:compiler:1.0.0"
//For LiveData, and ViewModel, add:
implementation "android.arch.lifecycle:extensions:1.0.0"
//For Room, add:
implementation "android.arch.persistence.room:runtime:1.0.0"
annotationProcessor "android.arch.persistence.room:compiler:1.0.0"
//For Paging add:
implementation "android.arch.paging:runtime:1.0.0-alpha3"

3、实现LifecycleObserver接口，通过注解方式添加resume、pause等回调接口
public class MyObserver implements LifecycleObserver {
    @OnLifecycleEvent(Lifecycle.Event.ON_RESUME)
    public void connectListener() {
        ...
    }

    @OnLifecycleEvent(Lifecycle.Event.ON_PAUSE)
    public void disconnectListener() {
        ...
    }
}


通过：myLifecycleOwner.getLifecycle().addObserver(new MyObserver());方法设置监听


http://www.jianshu.com/p/2fc41a310f79

https://mp.weixin.qq.com/s?__biz=MzAwODY4OTk2Mg==&mid=2652045083&idx=1&sn=3bd46870ded8e1c60bae88c0b3e52141&chksm=808d5f5eb7fad64840e415a4ca1049edfbfcdedae042e9360cdfd5c08525ef85ea222dc50189&mpshare=1&scene=23&srcid=1127DuYHlPR2nD9dxL3YJmMs#rd
