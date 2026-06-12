---
title: "problems with ushare installation"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by Ditchdoc7893 on 2011-02-22
Hello all.  So in trying to install ushare to be able to play my music and videos on my xbox 360, I have apparently screwed something up and now I can't get ushare to work.  I can't even get it uninstall and do a fresh install.  I used the instructions found here: [https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media).  I got down to the basic configuration tool.  I entered the name of the media server, which I called Ubuntu_Media_Server.  Then I identified my network interface, which was my wireless connection (wlan0).  Then I told it what directory to share, which was /home/ryan/music and hit enter.  It did exactly what it was supposed to do which was to restart ushare.  And then, oops, I forgot, I wanted to be able to see my videos as well as my music, so I went back and ran the same command that I had to start the configuration tool which was $ sudo dpkg-reconfigure ushare and voila, I went back and added in the directory for the video folder that I wanted to share and hit enter.  Again, it restarted as expected then it said permission was denied to the video folder.  So I went to the video folder and gave permission for it to be shared.  So then in all my illustrious wisdom (which apparently equates to dumbass), I decided to completely uninstall ushare and do a fresh install.  Then it wouldn't reinstall, same problem permission denied for the video file.  I have no idea what to do.  Can someone give me some step by step help on what to do to just start from scratch and not even include the video folder.  All I really care about is being able to play my music on the xbox 360.  Please help, thanks!

Ryan

---

