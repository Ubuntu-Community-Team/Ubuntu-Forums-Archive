---
title: "I need to learn HOW to do this???? please help"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by ConXtionS on 2009-10-02
Hi guys

I need to do this......

-------------------------------------------

 				 				**Re: Choppy Live TV** 			
 			 			 		   		 		 		newlinux you are a lifesaver.

I was wondering why the line:

/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext

kept coming up, and I was SURE I had the correct /etc/X11/XvMCConfig file.

However after going through it I noticed that I had originally created a file called XmVCConfig (not XvMCConfig). Pushing the "up" cursor on my terminal for commands for the past two weeks kept me making this mistake. (See my second post for the proof! :razz:)

I have changed it now - and - thankfully - the OSD is B&W, and my 1080i is displaying pretty well! It takes 5-6 seconds for the audio and video to sync up but after that I can't complain! 

Even HD basketball recordings are coming in clear! Anything above 70% signal strength comes in really well. March madness here I come.....

Thanks to all (esp. newlinux) for your help, and if anyone else is looking for a fix to this, here is the directions for my fix (note this only pertains to nvidia users):

1)  Make sure you have the correct driver to display XvMC.  Synaptic or Envy can do this.
2)  Change or create your /etc/X11/XvMCConfig file to display libXvMCNVIDIA_dynamic.so.1 
3)  Change your /etc/x11/xorg.conf file.  Make sure your driver is set to "nvidia" and not "nv".

Also, under device, add the lines:

Option "RenderAccel" "true"
Option "NVAGP" "0"
Option "UseEvents" "True"
Option "XvmcUsesTextures" "false"


Note - some people think putting a "1" or "2" into the NVAGP line works better for them.  

4) Set your playback profiles (as suggested by newlinux) to using standard xvmc decoder and xvmc-blit, 1CPU, bob 2x deinterlacer, and one field fallback deinterlacer.


For more info see 

[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

Everything you could think of will be on there.

Avoid Typos.  It will save time in the end :wink:

-----------------------------------------------------------

My problem is... I have no idea how to get to those files or edit them?

Help please????

thanks

Jim

---

### Post by Paddy Landau on 2009-10-02
To edit a file, you use gedit, or navigate there with nautilus (or through the Places menu).

However...

These files are owned by root, so you need special privileges.

There are a few different ways to go about getting the special privileges. Possibly the easiest, from a newbie point of view, is to start gedit with the privileges and then open the required file, as follows.

[LIST]
[*]Press Alt-F2, and type [FONT=Courier New]gksu gedit[/FONT].
[*]The computer will ask for your password before it opens gedit.
[*]Open the file that you want to edit.
[/LIST]
**WARNING:** You can easily mess up your system with that, so be extra careful until you close gedit.

---

### Post by Hospadar on 2009-10-02
First let me say, it will be easiest if you do things the way paddy landau suggests, it's much more visual and straightforward.

Second I think it would save you time in the long run to use the terminal and a text-mode editor.  Maybe not for this problem, but it's a great tool to have, the linux command line is waaay more powerful than it's windows counterpart.  There's a lot of information that can be quickly gotten from the terminal and it's a superb window into the underbelly of the system for times when you need to locate and solve problems.

let's say you wanted to edit xorg.conf for example (everything after # is a comment, don't actually type it in)

```

cd /etc/X11 #change directory to /etc/X11
sudo nano xorg.conf #sudo gives all the commands that follow it root (administrator) privilege.  This is needed because xorg.conf is owned by root.  nano is one of the easier text-based editors to use, Ctrl-o to save files, ctrl-x to exit.

```

Google for linux command line tutorials, there are many out there, they will help you familiarize yourself with basic commands and the general way of things in the terminal.

---

### Post by Paddy Landau on 2009-10-02
I agree with Hospadar about learning to use the terminal.

I would disagree with the choice of editor, though. Hospadar says to use nano:
[FONT=Courier New]    sudo nano xorg.conf[/FONT]
Whereas I would say use gedit:
[FONT=Courier New]    gksu gedit xorg.conf[/FONT]

Of course, you'll make up your own mind about which is easier for you.

It's best that you learn about *sudo* and *gksu*. sudo gives you (temporary) root permissions. So does gksu. The difference is that you *must* use gksu, not sudo, when using a graphical program. (The reasons can get quite technical, and I tend to forget why anyway, so I won't explain here.)

nano is not a graphical program, so you can use sudo or gksu.
gedit is a graphical program so you must use gksu.

For simplicity, you may want to always use gksu. Usually, that's perfectly fine.

By the way, you'll come across *gksudo* in these forums. gksudo is identical to gksu; they are different names for the same program.

You'll also come across *su*. I do not recommend that you use su.

---

### Post by ConXtionS on 2009-10-02
THANK YOU MUCH BROS

Ok... I can finally see the directory... I appreciate the help...





> **Hospadar said:**
> First let me say, it will be easiest if you do things the way paddy landau suggests, it's much more visual and straightforward.

Second I think it would save you time in the long run to use the terminal and a text-mode editor.  Maybe not for this problem, but it's a great tool to have, the linux command line is waaay more powerful than it's windows counterpart.  There's a lot of information that can be quickly gotten from the terminal and it's a superb window into the underbelly of the system for times when you need to locate and solve problems.

let's say you wanted to edit xorg.conf for example (everything after # is a comment, don't actually type it in)

```

cd /etc/X11 #change directory to /etc/X11
sudo nano xorg.conf #sudo gives all the commands that follow it root (administrator) privilege.  This is needed because xorg.conf is owned by root.  nano is one of the easier text-based editors to use, Ctrl-o to save files, ctrl-x to exit.

```Google for linux command line tutorials, there are many out there, they will help you familiarize yourself with basic commands and the general way of things in the terminal.

---

### Post by ConXtionS on 2009-10-02
lol 

I have no idea how to mark the thread as solved either

---

### Post by Paddy Landau on 2009-10-03
> **ConXtionS said:**
> I have no idea how to mark the thread as solved
Near the top, above your first post, you can see [COLOR=Red]_Thread Tools_[/COLOR]. Under that, you'll see "Mark this thread as solved."

---

