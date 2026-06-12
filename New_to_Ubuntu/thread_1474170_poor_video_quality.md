---
title: "poor video quality"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by noworldorder on 2010-05-05
I recently moved from windows to Ubuntu.  I noticed that the avi files seem to be of poorer quality on Ubuntu as compaired to windows.  Movement seems a bit less trhan fluit.

Anyone one else experienced this?  I am using Totem Movie Player 2.28.2

Thanks - chris

---

### Post by ubunterooster on 2010-05-05
I'm using 2.30.1. and it works fine; try updating.

---

### Post by shae on 2010-05-05
What video card and driver are you using?

---

### Post by madjr on 2010-05-05
never had a problem, try installing **VLC**

---

### Post by noworldorder on 2010-05-05
thanks for the replies - newbie question.  How do I update software...

---

### Post by ubunterooster on 2010-05-05
System>administration>update manager

Unless you prefer command line: ```
sudo apt-get update
```

---

### Post by dalee on 2010-05-05
Hi,

If you want to update, simply go to System-Administration-Update Manager.

If you meant that you want install VLC, just use System-Administration-Synaptic Package Manager. Click search and enter vlc. Then just mark it for installation.

dalee

---

### Post by ubuntu27 on 2010-05-05
What version of Ubuntu are you using? The current version is 10.04 and its codename is Lucid Lynx.

If you have Ubuntu 9.10 (Karmic Koala), follow this guide:

[http://www.howtoforge.com/how-to-upgrade-ubuntu-9.10-karmic-koala-to-10.04-lucid-lynx-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-9.10-karmic-koala-to-10.04-lucid-lynx-desktop-and-server)



But, before that. try to play your video with VLC Player. Many people believe VLC to be the best media player.

Since it is in the repositories, you can install it in the usual manner with Synaptic Package Manager, Ubuntu Software Center, apt, etc

---

### Post by noworldorder on 2010-05-05
update manager says my system is up to date even though Totem Movie Player 2.28.2 is not the latest version

---

### Post by Bob Appleby on 2010-05-05
Will VLC play netflix movies?

---

### Post by ubunterooster on 2010-05-05
Sorry, Bob . it will not.

---

### Post by noworldorder on 2010-05-05
So can anyone tell me how I get the latest verison of Toem MEdia Player i.e. update the one I have?

Thanks - chris

---

### Post by ubunterooster on 2010-05-05
Are you using Lucid?

---

### Post by noworldorder on 2010-05-05
and 'Lucid' is.....

sorry, I am supernewbie.  All I know is I have Ubuntu 9.10

---

### Post by lisati on 2010-05-05
> **noworldorder said:**
> and 'Lucid' is.....

sorry, I am supernewbie.  All I know is I have Ubuntu 9.10

"Lucid" is a name for 10.04. The version you have, 9.10, is sometimes referred to as "Karmic" or "Karmic Koala"

---

### Post by noworldorder on 2010-05-05
so given that I am using 9.10 how do I update Totam?

And should I switch to Lucid?  And if so do I have to start from scratch?

thanks - chris

---

### Post by ubunterooster on 2010-05-05
Go to Applications>accessories>terminal. 

type: sudo update-manager -d


Then press enter, give password, and press enter again.

There will be a button that allows you to upgrade to 10.04 in the update-manager.

---

### Post by noworldorder on 2010-05-06
**is it too late to stop installing?** 			
 			 			 		   		 		 		I have 9.10 working fine.  Thought I would upgrade to 10.04 then I read a few of the horror stories on the Lucid forum.

So far I have gone through:

preparing to upgrade
setting new software channels

and now I am getting new packages.

If I cancell now will I be okay?

Did any of the previous instalation steps do anything I need to reverce?

Should I be afraid to install?

Thanks - Chris

---

### Post by noworldorder on 2010-05-06
the choppy video was caused - it would seem - by the CompizConfig cube interface that was eating up too much processor.  Now the video is perfect!

---

### Post by madjr on 2010-05-06
if you ever want to upgrade check here (side by side install):

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

but if everything works fine, stick with it for a while

---

