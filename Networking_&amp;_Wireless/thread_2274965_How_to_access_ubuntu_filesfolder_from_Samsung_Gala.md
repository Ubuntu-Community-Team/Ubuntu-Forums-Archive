---
title: "How to access ubuntu files/folder from Samsung Galaxy Tab"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by jiggy79 on 2015-04-23
I'm trying to figure out to access files and folders on my ubuntu installed system. I have a Samsung Galaxy Tab 3 and I have access through windows 7 before but not a linux based system. Any suggestions would be greatly appreciated. Thanks

---

### Post by martin154 on 2015-04-23
i access mine using ES-explorer on the Galaxy Note. I right click on the folder I want to have access to and select settings, share options for the folder (dont know what it is called in english, my stuff is in German). now I can make the folder accessible. restart the computer and you should be able to see the folder on es explorer.

---

### Post by SeijiSensei on 2015-04-23
I use a variety of methods to exchange files with my Samsung Galaxy S3.  One is to connect the device directly using a USB cable.  

The other two options rely on wifi.  You can install the [Acrosync]("https://play.google.com/store/apps/details?id=com.acrosync.android.plus&hl=en") client from the Google Play store and exchange files with the Ubuntu box using the rsync protocol.  There's an rsync program on every Ubuntu box by default.  The other option is to install a DLNA server like [minidlna]("https://bugs.launchpad.net/ubuntu/+source/minidlna/+bug/1309651/comments/8") and use the [Bubble UPNP]("https://play.google.com/store/apps/details?id=com.bubblesoft.android.bubbleupnp&hl=en") client on Android.  That's designed more for streaming media than normal file exchanges though.

If you configure the Ubuntu box to use Samba to share files, you can connect with the [AndSMB]("https://play.google.com/store/apps/details?id=lysesoft.andsmb&hl=en") client.  The [AndFTP](https://play.google.com/store/apps/details?id=lysesoft.andftp&hl=en) client can also be configured to use the SCP protocol to copy files to and from the Ubuntu box.  Like rsync, that doesn't require installing Samba.

---

