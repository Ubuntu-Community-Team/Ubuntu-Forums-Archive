---
title: "firefox and ubuntu 610 hangs with wusb54g linksys wireless network card"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by robinsingh on 2007-01-29
I followed this thread [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)
and setup my edgy Ubuntu 610 to work with my wusb54G v4 drivers.

Now after almost 1.5 hours of online activity, firefox just hangs and whole OS just hangs on its own. I tried using swiftfox browser instead, that did give me faster performance than firefox but that too just hung up after 2 hours of continuous online work. Basically everytime it hangs, i am browsing around and my mouse pointer just freezes, keyboard just freezes, nothing is happening on the screen - all the stuff comes to standstill - OS hangs up basically. 

I just have to restart my machine then and the same happens after a couple of hours of online work. The OS is otherwise working perfectly before the hangup happens. This only started happening after i installed the wireless drivers after following the above thread.

After installing the drivers,I ran the commands (a  & b) (to make the wireless connection show up in Admin > networking  after a system restart)
       a)  sudo depmod
       b)  sudo modprobe ndiswrapper

Then I ran
       c)  ndiswrapper -m
so that I didnt have to re-run those commands (a and b) after every system restart. So now after every system restart my wireless network connection worked on its own.
But as i mentioned above, the system hangs up after around 2 hours of online activity through the firefox/swiftfox browser.
other than that, i dont understand what could be the problem. 

Any help would be much appreciated. I was 100% done with hosting my personal website on this linux server, but this hang up issue is causing me to switch back to windowsxp os to host my server (but i only want to run it on linux :-)

---

### Post by Arlanthir on 2007-04-01
I haven't installed any wireless drivers but my firefox makes ubuntu hang sometimes too.. Never knew what really caused it though..

---

