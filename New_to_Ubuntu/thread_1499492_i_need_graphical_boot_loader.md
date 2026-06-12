---
title: "i need graphical boot loader"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by munna.cheyur on 2010-06-02
I'm using 10.04 as in previous versions the default boot loader is in only text mode... I wan't nice graphical grub boot loader... How to apply this. Where to download.

---

### Post by ankspo71 on 2010-06-02
Hi,
I never done this before but I found a link here:
[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

I found it in here: (which has more ideas for you to try)
[http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)
Hope this helps.

---

### Post by nhasian on 2010-06-02
from what i understand, grub2 gives us the ability to have fancier graphical boot menus.

take a look at [http://grub.gibibit.com/](http://grub.gibibit.com/)

---

### Post by KermEd on 2010-06-02
A lot of this stuff is hands on with GRUB2.

You can specify just a background image and customize the text to use (and resolution) fairly easily.  Its always a good idea to change your boot loader resolution to match your OS resolution whenever possible and if the hardware permits.

**Changing Resolution**

> gksudo gedit /etc/grub.d/00_headerThis should open your basic options for GRUB2.   Find the following entry:

> set gfxmode=[COLOR=Navy]640x480[/COLOR]And change it to your desired [COLOR=Navy]graphic [/COLOR]mode (ie:  [COLOR=Navy]1024x768[/COLOR]).  Remember, this value must match your image (below).  


**Image Background and Custom Colours**

> gksudo gedit /etc/grub.d/05_debian_themeIn here browse downwards until you see:

> 
 for i in {[COLOR=DarkGreen]/boot/grub,/usr/share/images/desktop-base[/COLOR]}/[COLOR=DarkRed]moreblue-orbit-grub[/COLOR].{[COLOR=Navy]png,tga[/COLOR]}
[COLOR=DarkGreen]This is the folders it will look for the image. [/COLOR] Place your image in /boot/grub in case the boot loader cannot access your user/share folder.

[COLOR=DarkRed]This is the name of your file[/COLOR] - ie: for [COLOR=Black]Picture12.jpg[/COLOR], you would put [COLOR=DarkRed]Picture [/COLOR]here.

[COLOR=Navy]These are the allowed types[/COLOR], so if you want to use a [COLOR=Navy]jpg[/COLOR], add it to the list.

So - lets say I added Picture12.jpg to /boot/grub.  The picture should be the size of the bootloader window (640x480 by default I believe).  I would change this line to read:

> 
 for i in {[COLOR=DarkGreen]/boot/grub,/usr/share/images/desktop-base[/COLOR]}/[COLOR=DarkRed]Picture12[/COLOR].{[COLOR=Navy]png,tga,jpg[/COLOR]}
So far so good?  Okay, but now that we've added a picture, it will change the GRUB menu colours.  We need to adjust this next - scroll down more.  Make sure you keep that dot in the filename.  If  the image doesnt show on a reboot - it means you made a mistake in this line, the image is incompatible, or the file couldnt be found.

> if background_image `make_system_path_relative_to_its_root ${bg}` ; then   set color_normal=[COLOR=Navy]black[/COLOR]/[COLOR=DarkRed]black[/COLOR]   set color_highlight=light-red/blackIn [COLOR=Navy]foreground [/COLOR]/ [COLOR=DarkRed]background [/COLOR]format.  In my case my screen is dark for the .JPG so I changed this to read:  

>  if background_image `make_system_path_relative_to_its_root ${bg}` ; then    set color_normal=white/[COLOR=DarkRed]black[/COLOR]    set color_highlight=light-red/black Easy enough, so now you have custom colours and a custom image.

Now we just need to tell it to update itself:

9.04/9.10:  > sudo grub-mkconfig -o /boot/grub/grub.cfg10.04:  > sudo update-grub2And voila!  Now, if you want to get more complex than that - your going to really need to dig into GRUB2 - I dont think there is a quick utility for it at the moment.

The more advanced changes you should be able to pick up here and there.  Someone placed a link to a handy website - it has some example code you can preview - but I imagine (because there isn't an all-in-one utility at the moment) you might be better off doing it by hand.

- Lloyd

---

### Post by yetiman64 on 2010-06-02
@ KermEd, to use sudo with any grapical process (in this case gedit), gksudo (or gksu) should be used. Please check the [RootSudo]("https://help.ubuntu.com/community/RootSudo") link and refer to the Graphical Sudo section down the page a bit. You may need to edit your commands given where necessary.

Note that normal terminal commands are fine with sudo though.

 Cheers.

---

### Post by KermEd on 2010-06-02
Thanks Yeti,

I've only been using it about a week and a half.  I wondered what that difference was.

---

### Post by yetiman64 on 2010-06-02
> **KermEd said:**
> Thanks Yeti,

You're welcome. :)

---

