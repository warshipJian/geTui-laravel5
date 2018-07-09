个推laravel5扩展包, 根据官方SDK包整理

安装
----
```
composer require warship-jian/ge-tui-laravel5
```

使用
----
```
$key = 'abcddefg';
$url = 'http://sdk.open.api.igexin.com/apiex.htm';
$mastersecret = 'abc123456';
$appid = '123456';

$cid = 'abcdef'; //客户端的cid

$gePush = new GetuiPush($url,$key,$mastersecret);

$template = new IGtNotificationTemplate();
$template->set_appId($appid);                   //应用appid
$template->set_appkey($key);                 //应用appkey
$template->set_transmissionType(1);            //透传消息类型
$template->set_transmissionContent('透传内容'); //透传内容
$template->set_title('标题内容');       //通知栏标题
$template->set_text('通知栏内容');     //通知栏内容
$template->set_logo("");                       //通知栏logo
$template->set_logoURL("");                    //通知栏logo链接
$template->set_isRing(true);                   //是否响铃
$template->set_isVibrate(true);                //是否震动
$template->set_isClearable(true);              //通知栏是否可清除

$message = new IGtAppMessage();
$message->set_isOffline(true);
$message->set_offlineExpireTime(10 * 60 * 1000);//离线时间单位为毫秒，例，两个小时离线为3600*1000*2
$message->set_data($template);

$target = new IGtTarget();
$target->set_appId($appid);
$target->set_clientId($cid);

//推送
$gePush->pushMessageToSingle($message,$target);

```
