---
title: "Problems with last.fm/rythmbox"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by charlie651 on 2009-03-03
Hi, I am new to linux but i just got a laptop with ubuntu hardy heron on it and am trying to set it up. I really want to get the last.fm player working, and i have installed it using
'sudo apt-get install lastfm'

it seems to have installed fine, it shows up in my menus and everything, but when i run it i get a message,
"Couldn't load radio service 'httpinput'. The radio will not work."
and i cant get it to play any music.

I have looked this up and it seems like some other people have had this problem, and solved it by finding fixing broken library links but i am not sure how to do this...

The laptop also has rhthmbox installed, and this is also unable to play last.fm through the plugin!..

Has anyone else got this to work on ubuntu? Anyone had this problem? Any idea how to fix it?

if it helps, the laptop is a dell mini 9 and its running ubuntu 8.04.

Thanks!

---

### Post by Ms_Angel_D on 2009-03-03
Hi I did a google search for your error and came up with this post in the Last.fm forums you might wanna check it out.

[http://www.last.fm/forum/34905/_/365911](http://www.last.fm/forum/34905/_/365911)

Wish I could be be of more assistence.

Angel

---

### Post by charlie651 on 2009-03-03
Hey, that is the same thread i was looking at.  It seems like some people had this problem because of confusion between lib and lib64 directories, but i don't have any /usr/lib64 directory.  Maybe there is something on ubuntu that could cause similar confusion w/ the libraries?

I actually posted the same question in the last.fm forum too, but it seems like there arent too many linux users there so i posted here as well..

---

### Post by charlie651 on 2009-03-03
This is the log from /home/charlie/.local/share/Last.fm/Last.fm.log

i checked to make sure that /usr/lib/lastfm/libserv_httpinput.so was there and it does exist


90304 02:19:25 - 3062531904 - Init(164) - L1
  ************************************* STARTUP ********************************************

090304 02:19:25 - 3062531904 - Init(165) - L1
  OS: Unix/Linux

090304 02:19:25 - 3062531904 - Init(172) - L2
  No default message handler found, using our own.

090304 02:19:25 - 3062531904 - initLogger(338) - L1
  App version: 1.4.2.58240

090304 02:19:25 - 3062531904 - setLanguage(368) - L3
  Setting language to: en

090304 02:19:25 - 3062531904 - WebService(39) - L3
  Initialising Web Service

"090304 02:19:25" - "-1232435392" - void WebService::autoDetectProxy() ( 187 ) - L4
   

"090304 02:19:25" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
   "Proxy Test" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

"090304 02:19:25" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
   "Proxy Test" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

090304 02:19:25 - 3060984720 - OpenSocket(418) - L3
  Listener bound to port 33367

"090304 02:19:25" - "-1242375280" - QObject* AudioControllerThread::loadPlugin(QString) ( 197 ) - L4
   "/usr/lib/lastfm/libsrv_httpinput.so" 

090304 02:19:25 - 3062531904 - resetWidget(357) - L3
  Launching login dialog mode CHANGE_PASS

"090304 02:19:26" - "-1232435392" - MetaDataWidget::MetaDataWidget(QWidget*) ( 100 ) - L4
   Detected default: "Sans Serif,9,-1,5,50,0,0,0,0,0" 

"090304 02:19:26" - "-1232435392" - void Container::setupTrayIcon() ( 241 ) - L4
   

090304 02:19:26 - 3062531904 - LoadIcons(153) - L4
  Icons loaded

"090304 02:19:26" - "-1232435392" - void Container::updateAppearance() ( 1142 ) - L4
   

090304 02:19:26 - 3062531904 - stop(735) - L4
  AudioController requesting stop of 

090304 02:19:26 - 3062531904 - setState(907) - L4
  AudioController state: State_Stopping

"090304 02:19:26" - "-1232435392" - void Container::updateUserStuff(LastFmUserSettings&) ( 1120 ) - L4
   

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "Friends" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/friends.xml?imagesize=small" 

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "Neighbours" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/neighbours.xml?imagesize=small" 

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "UserTags" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/tags.xml" 

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "RecentTracksRequest" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recenttracks.xml" 

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "RecentlyLovedTracks" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recentlovedtracks.xml" 

"090304 02:19:26" - "-1232435392" - void Request::request(const XmlRpc&) ( 262 ) - L4
   "UserPictures" initiated: "ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "RecentlyBannedTracks" initiated: "ws.audioscrobbler.com/1.0/user/Charlie651/recentbannedtracks.xml" 

090304 02:19:26 - 3062531904 - stop(483) - L3
  Stopping radio

090304 02:19:26 - 3062531904 - setState(667) - L4
  Radio state: State_Stopped

"090304 02:19:26" - "-1232435392" - void Request::get(QString) ( 217 ) - L4
   "Handshake" initiated: "ws.audioscrobbler.com/radio/handshake.php?version=1.4.2.58240&platform=linux&platformversion=Unix%2FLinux&username=Charlie651&passwordmd5=1799432518ec7132b60dd026816ad048&language=en" 

090304 02:19:26 - 3062531904 - setState(667) - L4
  Radio state: State_Handshaking

"090304 02:19:26" - "-1232435392" - void ScrobblerManager::handshake(const Scrobbler::Init&) ( 76 ) - L4
   "Charlie651" 

"090304 02:19:26" - "-1232435392" - Scrobbler::Scrobbler(const Scrobbler::Init&) ( 502 ) - L4
   Initiating Scrobbler handshake for: "Charlie651" 

"090304 02:19:26" - "-1232435392" - virtual void ScrobblerHandshakeRequest::request() ( 842 ) - L4
   GET: "?hs=true&p=1.2&c=***&v=1.4.2.58240&u=Charlie651&t=1236133166&a=e1a8c002306829e0f06ce44dc004db46" 

Waiting on CachedHttpJanitor thread! 

Waiting on CachedHttpJanitor finished! 

"090304 02:19:27" - "-1232435392" - QWidget* mainWindow() ( 36 ) - L4
   (Container(0x8210268, name = "MainWindow") ,  ShareDialog(0x8211810, name = "ShareDialog") ,  SettingsDialog(0x8255d90, name = "SettingsDialog") ,  QMenu(0xb37c6090) ,  DiagnosticsDialog(0x82f3a20, name = "DiagnosticsDialog") ,  QMenu(0x83fc1c0) ,  QMenu(0x83e9078, name = "menuFile") ,  QMenu(0x83e8e98, name = "menuView") ,  QMenu(0x83ea0a8, name = "menuControls") ,  QMenu(0x83e7f00, name = "menuHelp") ,  QMenu(0x83ea520, name = "menuUser") ,  QMenu(0x83eabd8, name = "menuTools") ,  QLabel(0x8428470) ,  QComboBoxPrivateContainer(0x824f718) ,  QComboBoxPrivateContainer(0x82f67c0) ,  QComboBoxPrivateContainer(0x8253cc8) ,  QComboBoxPrivateContainer(0x822d780) )  

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Proxy Test" response: 302 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "Proxy Test"  request succeeded 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recenttracks.xml" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "RecentTracksRequest" response: 302 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "RecentTracksRequest"  request succeeded 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/neighbours.xml?imagesize=small" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Neighbours" response: 302 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Proxy Test" response: 302 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/tags.xml" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "UserTags" response: 302 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/rw/xmlrpc.php" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "UserPictures" response: 302 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/radio/handshake.php?version=1.4.2.58240&platform=linux&platformversion=Unix/Linux&username=Charlie651&passwordmd5=1799432518ec7132b60dd026816ad048&language=en" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Handshake" response: 302 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "Proxy Test"  request succeeded 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "UserTags"  request succeeded 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "UserPictures"  request succeeded 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "Handshake"  request succeeded 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/friends.xml?imagesize=small" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Friends" response: 302 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recentbannedtracks.xml" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "RecentlyBannedTracks" response: 302 

090304 02:19:27 - 3062531904 - setState(667) - L4
  Radio state: State_Uninitialised

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "Friends"  request succeeded 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "RecentlyBannedTracks"  request succeeded 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://ws.audioscrobbler.com/1.0/user/Charlie651/recentlovedtracks.xml" 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "RecentlyLovedTracks" response: 302 

090304 02:19:27 - 3062531904 - onRadioError(883) - L2
  Radio error 4: The Last.fm servers are temporarily overloaded, please try again in a moment.

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "RecentlyLovedTracks"  request succeeded 

Http request returned redirect (301, 302 or 307):  "http://wireless.netaccess.umn.edu/aaa/uofm.html?wbaredirect=http://post.audioscrobbler.com/?hs=true&p=1.2&c=***&v=1.4.2.58240&u=Charlie651&t=1236133166&a=e1a8c002306829e0f06ce44dc004db46" 

"090304 02:19:27" - "-1232435392" - void Scrobbler::hardFailure() ( 523 ) - L4
   Scrobbler HTTP error: 49 

"090304 02:19:27" - "-1232435392" - void Scrobbler::hardFailure() ( 537 ) - L4
   Scrobbler hard failure. Retrying in 30 seconds. 

"090304 02:19:27" - "-1232435392" - void Request::onHeaderReceivedPrivate(const QHttpResponseHeader&) ( 102 ) - L4
   "Neighbours" response: 200 

"090304 02:19:27" - "-1232435392" - void Request::onSuccessPrivate(QByteArray) ( 182 ) - L4
   "Neighbours"  request succeeded 

090304 02:19:37 - 3062531904 - onRadioError(883) - L2
  Radio error 1009: Couldn't load radio service 'httpinput'. The radio will not work.

---

### Post by charlie651 on 2009-03-04
this is maybe not an absolute beginner problem?  is there a better section of the forum i should post this in?

---

