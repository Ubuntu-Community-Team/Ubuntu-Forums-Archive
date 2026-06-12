---
title: "installing realplayer"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by fifthwheel on 2008-12-26
I have looked through a lot of old posts before posting this but the answers I see seem to be for more experienced users. I dont understand the terminal properly or know how to make a file executable, I have realplayer downloaded to desktop but I cant seem to install it, I have googled for the answer but all the links seem complicated to me any simple steps would be appreciated. I need realplayer to listen to bbc radio (UK) thanks.

---

### Post by sportscrazed2 on 2008-12-26
yeah same here i tried but it gets stuck at installing dependencies.  shame i had to boot windows just to rip a song to my mp3 player

---

### Post by LowSky on 2008-12-26
[http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

download this then click to install, just like in windows

---

### Post by candtalan on 2008-12-26
> **fifthwheel said:**
> but all the links seem complicated to me any simple steps would be appreciated. I need realplayer to listen to bbc radio (UK) thanks.

realplayer can be installed however it is not essential, you can play what you want using mplayer I believe, and with Ubuntu version 8.10, it will either play out of the box after install immediately or it will ask you if you are happy for it to get the codecs automatically  and it will install them, automatically.

Which ubuntu version are you using?

If you really want to use Realplayer, that is ok.
Which realplayer file are you thinking of using?

---

### Post by LowSky on 2008-12-26
> **sportscrazed2 said:**
> yeah same here i tried but it gets stuck at installing dependencies.  shame i had to boot windows just to rip a song to my mp3 player

what dependences?
mp3 support is easy to get go to add/remove
look up ubuntu

install ubuntu restricted extras

you now have mp3 support, flash, Microsoft fonts, java, and a few more things

there are like 5 programs that can rip a song, banshee, exaile, amarok, sound juicer...

---

### Post by sportscrazed2 on 2008-12-26
> **LowSky said:**
> what dependences?
mp3 support is easy to get go to add/remove
look up ubuntu

install ubuntu restricted extras

you now have mp3 support, flash, Microsoft fonts, java, and a few more things

there are like 5 programs that can rip a song, banshee, exaile, amarok, sound juicer...

i have no idea to be honest but the only reason i was trying to install it was to rip cds which i use it for in windows but i found a better freeware called sound juicer so i won't worry about it

---

### Post by sayems on 2008-12-26
To install RealPlayer first download **RealPlayer10GOLD.bin** file from [http://www.real.com/linux/]("http://www.real.com/linux/") assuming you have downloaded it to your home directory .

After downloading the file go to the directory where you have downloaded the file in terminal window and type

After installation is over type

¨chmod +x RealPlayer10GOLD.bin¨

and

¨sudo ./RealPlayer10GOLD.bin¨

for installation to begin . Follow the instructions as presented to complete installation .

---

### Post by LowSky on 2008-12-26
> **sayems said:**
> To install RealPlayer first download **RealPlayer10GOLD.bin** file from [http://www.real.com/linux/]("http://www.real.com/linux/") assuming you have downloaded it to your home directory .

After downloading the file go to the directory where you have downloaded the file in terminal window and type

After installation is over type

¨chmod +x RealPlayer10GOLD.bin¨

and

¨sudo ./RealPlayer10GOLD.bin¨

for installation to begin . Follow the instructions as presented to complete installation .

sayems, I posted the link to the .deb file, which is much easier to install then the bin file.

---

### Post by fifthwheel on 2008-12-26
> **LowSky said:**
> [http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb](http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb)

download this then click to install, just like in windows

I have just tried to install your link but it asked for my Ubuntu 8.04 cd but i dont have it, I do have the latest cd 8.10 do you advise a clean install if so will all my stuff be in the same place or will it all be wiped? The BBC website will not let me listen again to an old show without realplayer

---

### Post by sportscrazed2 on 2008-12-26
> **LowSky said:**
> sayems, I posted the link to the .deb file, which is much easier to install then the bin file.

yeah man thats what i tried using before but it would lock up before install would finish

---

### Post by oldos2er on 2008-12-26
> **fifthwheel said:**
> I have looked through a lot of old posts before posting this but the answers I see seem to be for more experienced users. I dont understand the terminal properly or know how to make a file executable, I have realplayer downloaded to desktop but I cant seem to install it, I have googled for the answer but all the links seem complicated to me any simple steps would be appreciated. I need realplayer to listen to bbc radio (UK) thanks.

 Open up a terminal, and run these commands one at a time:

 cd Desktop

 chmod a+x RealPlayer11GOLD.bin

 sudo ./RealPlayer11GOLD.bin

 Follow the instructions. Quit the installer program, and run Applications, Sound & Video, RealPlayer 11.

---

### Post by fifthwheel on 2008-12-26
Have tried putting the info into the terminal but I get no such file or directory. Realplayer shows in applications/sound and video but when I try to listen to music on the bbc website it still asks me to download realplayer. I have looked in add/remove programs but cant see it installed

---

### Post by sayems on 2008-12-26
**Can RealPlayer be installed on a Linux / Unix computer?**

Yes. There are versions of RealPlayer made specifically for Linux and Unix based computers, as well as an open source Helix Player.
 
However, some users have found that the RealPlayer plug-in, which is used by the BBC Player, may or may not function fully depending on a combination of what flavour of Unix/Linux you are using, which browser you are using, which version of browser you are using, and which version of GCC built the plug-in during installation. 

You may find that you are only able to listen by following the &#8220;Listen using stand-alone RealPlayer&#8221; links within the BBC Player.
How to download and install
Linux

If you are using Linux/Unix, we recommend that you install RealPlayer 11. You can download this for free at Real.com.
Download RealPlayer 11 for Linux/Unix
Installing RealPlayer in Ubuntu

James Cridland, Head of Future Media & Technology, BBC Audio & Music Interactive, has provided a helpgul step-by-step guide to installing RealPlayer on Ubuntu:

1. Open Synaptic
Synaptic is the software that will install Real Player for you.
- Run System > Administration > Synaptic Package Manager.
- Type your password when it asks you.

2. Tell Ubuntu where to find commercial software
Real Player is commercial software, so we need to tell Ubuntu how it can find that if we search for it.
- Under the 'Settings' menu, choose 'Repositories'.
- Click the 'Third party software' tab.
- Click the 'Add' button at the bottom of the window.
- In the window that appears, type:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid-commercial main
- Then click 'OK' to enter that information, and 'close'.
- A window will appear saying that the repositories have changed.
- Click 'close'.
- Click the 'reload' button on the top-left of the toolbar.
- After a few seconds, it&#8217;ll load a few files.

3. Install Real Player
Now Synaptic will know all about commercial software, like Real Player. (Don&#8217;t worry, it&#8217;s still a free download).
- Hit the 'search' icon in the toolbar, and search for 'realplay'.
- You&#8217;ll see a few programs appear in the search results window. Tick the one called 'realplay' and choose 'Mark for Installation'.
- Then press 'Apply' in the toolbar;  then 'apply' again.
- Synaptic will automatically download a file (6 megabytes).
- Close your browser while it's doing this, so it can install correctly.
- Synaptic will automatically install Real Player onto your system.

4. Open BBC iPlayer to start listening
- Open your browser
- Visit [http://www.bbc.co.uk/radio/aod](http://www.bbc.co.uk/radio/aod) 
- Choose a station or programme to listen to.
- Enjoy.
Other Unix platforms

RealPlayer 11 for Linux is based on the open source Helix player. Versions of RealPlayer for other Unix platforms are available through the
Helix Community site

Find out more about the Helix Community Project.

[http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml]("http://www.bbc.co.uk/radio/help/faq/linux_and_unix_compatibility.shtml")

---

### Post by fifthwheel on 2008-12-26
I got some kind of error after following the last instructions something about line 31 I think. I have tried all day and my heads in a spin I am giving in but thanks to everybody for the help.

---

