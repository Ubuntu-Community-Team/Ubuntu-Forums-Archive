---
title: "Having problems getting broadcam set up"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by daimere on 2008-10-18
I have ubuntu.  I am very unfamiliar with ubuntu. Originally, it wouldn't let me online even wired.

 I used this thread: [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") using the Dapper and Edgy (and Feisty/Gutsy with ndiswrapper) method.  This let me get online via a wire.

I tried these two methods:
[http://tsupra88.blogspot.com/]("http://tsupra88.blogspot.com/").  Neither worked.

Although ONE of these methods, I am unsure of which, made the wireless icon by the on button of my laptop turn on but it didn't let it get online yet.

I tried this method:
[http://ubuntuforums.org/showpost.php?p=1189681&postcount=105]("http://ubuntuforums.org/showpost.php?p=1189681&postcount=105")
But because of all my other attempts, I didn't work because when I got to the go to networks, the wireless option which was always there before, wasn't there.

Somewhere along the way, that blue light also is gone.  I don't know when it stopped showing because I don't usually notice it that is why I don't know when it showed up or left.

This is the version broadcom I have:
[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-1.png[/IMG]

Can anyone help me? 
 It's not fun dragging my laptop around a long cord around my house just for the internet. lol  Thanks!


My lastest try at fixing this was using this tutorial:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

I ran into problems when I came to step 3 and finally at 5.  This is all the history of my terminal.

(I'm not sure if they are in order consider I didn't name them and I closed the terminal down jsut now)

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-5.png[/IMG]

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-4.png[/IMG]



[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-1-4.png[/IMG]

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-4.png[/IMG]

[IMG]http://i28.photobucket.com/albums/c207/daimere/Screenshot-3-1.png[/IMG]

[http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-6.png]("http://i28.photobucket.com/albums/c207/daimere/Screenshot-shannonshannon-laptop-6.png")





Please help me.  I really want wireless.

---

### Post by Ayuthia on 2008-10-18
Most likely linux-headers have already been installed.  Try the following:
```
uname -r
aptitude search linux-headers
```
Most likely you will find out that linux-headers-`uname -r` will have an i in front of it.  That means that it is already installed.

If you are not for sure, please post the results of:
```
uname -r
aptitude search linux-headers
```

I can possibly get ndiswrapper installed for you, but I am not 100% certain whether I can get your card going or not.  The 4318 cards have been difficult to get working in Hardy.

---

