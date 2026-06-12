---
title: "How do I save a document onto a flash drive?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Texas2009 on 2009-03-24
I am brand spankin' new to Ubuntu.  I've used Windows my entire life and I'm starting to regret trying something new.  Ubuntu is Greek to me. Some of the simpliest activities have turned into a hair pulling exercises!  I used openoffice.org to type up a document and I have no idea how to save it directly onto a flash drive. I resorted to saving it directly to the computer and cutting and pasting into my flash drive.  There has to be an easier way.  Help! I'm so used to clicking file - save as - and then simply clicking the drive.  Also, is there an equivalent to "ctrl Alt Delete" when your computer is frozen?

---

### Post by gandaran on 2009-03-24
> **Texas2009 said:**
> I am brand spankin' new to Ubuntu.  I've used Windows my entire life and I'm starting to regret trying something new.  Ubuntu is Greek to me. Some of the simpliest activities have turned into a hair pulling exercises!  I used openoffice.org to type up a document and I have no idea how to save it directly onto a flash drive. I resorted to saving it directly to the computer and cutting and pasting into my flash drive.  There has to be an easier way.  Help! I'm so used to clicking file - save as - and then simply clicking the drive.  Also, is there an equivalent to "ctrl Alt Delete" when your computer is frozen?
you sound just just like the typical windows user, doesn't know anything about operating systems and if you don't have an open mind and not willing to learn new things then ubuntu is not for you! 
when you choose -save as- in open office the first line gives you the save format option, be it  an open office format or windows compatible format, the second line is where you save the file to just choose the flash drive if thats what you want.

---

### Post by FraggedLocust on 2009-03-24
If you can paste it straight to the flash drive(in ubuntu, I'm assuming), why are you having difficulties finding that folder under the save menu? You should be able to save the document in openoffice using File>Save just like windows.

---

### Post by kanikilu on 2009-03-24
When you plug your flash drive in, does it get auto-mounted? Do you see an icon for it appear on your desktop?

If you go to File > Save As, you should see the flash drive listed under Places, using the same name as the icon on your desktop.

As for CTRL+ALT+DEL. The short answer is "no", there isn't a key-combination that brings up a "task manager" equivalent. However, if your computer is locked up, you can try a few things. First, try to open up the system monitor by pressing ALT+F2 and typing *gnome-system-monitor*.

If that doesn't work you may try to get into another virtual terminal using CTRL+ALT+F1, for example. From there, you can log in, and use *top* to view the running processes. If you know what's causing the problem, you can get the process ID and then end it with *kill <proccessID>*. You can also use *ps -ef | grep <search>* to search for processes meeting a particular criteria. You can also use *pkill <name>* if you know the name of the process (or at least part of it). For example if you know firefox is causing a problem, *pkill firefox* should work, rather than having to search out the process ID.

As a last resort, you can try CTRL+ALT+Backspace, which should end your current session and take you back to the login screen.

After that, a hard-reboot may be your only option.

---

### Post by mikeize on 2009-03-24
When you click "save as", over in the left pane of the window that pops up... you can look through all your available drives.  Your flash drive should be there, it may have a funny name, like "usb drive", or "diesel", "sandisk", etc.

*also, give this guy a break.  He's obviously open-minded enough to try something new, after using Windows his whole life, and is bound to be a little frustrated while he learns some new things.  You never get frustrated?

---

### Post by kanikilu on 2009-03-24
> **gandaran said:**
> if you don't have an open mind and not willing to learn new things then ubuntu is not for you! I'll let him speak for himself, but I'm not sure that's completely fair. It seems like he's a bit frustrated but not *unwilling* to learn. Everyone making the move from one OS to another is surely going to run into problems or have some questions.

To the OP, remember that just because something is simple in one OS and becomes second nature, doesn't *necessarily* mean it's simple in every OS. In Ubuntu, to install a new application, for example it (generally) takes a very short and simple command: *sudo apt-get install thunderbird*. In Windows, you have to open a web browser, find the software, download it, find where you downloaded it, and then run the installer (which in itself is usually a few steps). I don't want to turn this into a Windows v. Linux debate, but rest assured, once you start to get the hang of things, learn how things work, and to some degree start to utilize the power of the command line, you'll eventually find yourself regretting all the time you wasted on "that other OS" ;)

---

### Post by carml on 2009-03-24
There also a button you can add to the top panel to force to quit a non responding software. :)

---

### Post by gandaran on 2009-03-24
> I'll let him speak for himself, but I'm not sure that's completely fair. It seems like he's a bit frustrated but not unwilling to learn. Everyone making the move from one OS to another is surely going to run into problems or have some questions.
most windows users are frustrated when they encounter something new! the other day I went with a cousin that has a computer repair shop to a costumer that has always used microsoft office 2003, my cousin installed microsoft office 2007 when he repaired the computer, now the customer was fuming mad, he just didn't know how to use the new 2007 office!

---

### Post by Temposs on 2009-03-24
> **gandaran said:**
> most windows users are frustrated when they encounter something new! the other day I went with a cousin that has a computer repair shop to a costumer that has always used microsoft office 2003, my cousin installed microsoft office 2007 when he repaired the computer, now the customer was fuming mad, he just didn't know how to use the new 2007 office!

You are making the wrong generalization. It's not Windows users that get frustrated when they see something new. It's non-computer geeks and otherwise most people not technically oriented. Most people don't know how to use computers. They mostly memorize where buttons and menus and programs are, and if anything at all changes about the interface, they'll be completely lost.

If you teach a non-computer geek to use a computer with Ubuntu(like I've done with my Mom, for instance), and then put them on a Windows machine, they'll be equally as lost!

Just because there is a preponderance of computer geeks using Ubuntu doesn't mean using Ubuntu magically makes you a flexible learner and knowledgable about OSes and computers generally.

---

### Post by Texas2009 on 2009-03-24
Thank you to the people that had only kind, helpful suggestions.  To clear things up, this "he" is a "she", and I'm fresh out of college (where they only used windows).  Yes, I'm am a very computer challenged and I know I have a lot of learning and catching up to do.  Frustrated as I am, I am open to learning and expanding my horizons.  I just use my computer for pretty much two things: using MS Office/Open Office for work and surfing the internet.  I came here for help, not judgement.

Anyways, the point of this thread is that I can't seem to find my flash drive when I try to save something in open office.  When I click "Save As", I get the choices "desktop, documents, pictures, music, videos, etc."  If I back track, I get "bin, boot, dev, etc, home, initrd, etc."  and that's pretty much it.  I've looked inside all of these files and the flash drive is nowhere.  The only place I can find it is if I get to the desktop and click places.

---

### Post by philinux on 2009-03-24
When you backtrack look under the folder /media

---

### Post by kanikilu on 2009-03-24
When I use Save As in Open Office (I'm in Writer right now), I get:

Name:
Save in Folder: [drop down menu]
>Browse for other folders
...

Both in the Save in Folder, and in the Browse for other folders, my flash drive shows up. In my case it says "PATRIOT" because that's the brand. In your case, it might say something else (including something like "1.0GB Media", with the size). I've attached a screen shot...does yours not have anything like that?

As a last resort, you should be able to browse to it manually. It should be in a sub-directory of /media by default.

---

### Post by Temposs on 2009-03-24
> **Texas2009 said:**
> Thank you to the people that had only kind, helpful suggestions.  To clear things up, this "he" is a "she", and I'm fresh out of college (where they only used windows).  Yes, I'm am a very computer challenged and I know I have a lot of learning and catching up to do.  Frustrated as I am, I am open to learning and expanding my horizons.  I just use my computer for pretty much two things: using MS Office/Open Office for work and surfing the internet.  I came here for help, not judgement.

Anyways, the point of this thread is that I can't seem to find my flash drive when I try to save something in open office.  When I click "Save As", I get the choices "desktop, documents, pictures, music, videos, etc."  If I back track, I get "bin, boot, dev, etc, home, initrd, etc."  and that's pretty much it.  I've looked inside all of these files and the flash drive is nowhere.  The only place I can find it is if I get to the desktop and click places.

It's perfectly fine to be just a computer user and use Ubuntu. We're trying to make it more usable everyday :-) Most people on these forums are quite helpful and non-judgmental.

As the above post states, if your flash drive is indeed working on your machine, you will be able to see it as a folder in /media.  Often, flash drives and such are listed there as /media/disk, or something similar.

If you don't see anything like that, please tell us so we can help you further.

---

### Post by gandaran on 2009-03-24
> **Texas2009 said:**
> Thank you to the people that had only kind, helpful suggestions.  To clear things up, this "he" is a "she", and I'm fresh out of college (where they only used windows).  Yes, I'm am a very computer challenged and I know I have a lot of learning and catching up to do.  Frustrated as I am, I am open to learning and expanding my horizons.  I just use my computer for pretty much two things: using MS Office/Open Office for work and surfing the internet.  I came here for help, not judgement.

Anyways, the point of this thread is that I can't seem to find my flash drive when I try to save something in open office.  When I click "Save As", I get the choices "desktop, documents, pictures, music, videos, etc."  If I back track, I get "bin, boot, dev, etc, home, initrd, etc."  and that's pretty much it.  I've looked inside all of these files and the flash drive is nowhere.  The only place I can find it is if I get to the desktop and click places.
okay Texas2009, this is a friendly suggestion, open terminal and type **gconf-editor** (or system » preferences » main menu » system tools, enable configuration-editor) go to apps » nautilus » desktop, enable volumes_visible, your flash drive will now mount on desktop, maybe this will make the deference and more easy to locate the flash drive.

---

### Post by Texas2009 on 2009-03-24
Thanks so much, guys!  That "media" thing worked!  I really appreciate your time and patience with me.  Gandaran, thanks for your suggestion as well.  I'm going to try to mount that onto my desktop.

---

### Post by sgosnell on 2009-03-24
Yes, give her a break.  She apparently went to UT, and is thus severely handicapped.  If she had gone to one of the better universities in the state, she might be more informed.  :p  :tongue:  :D   :popcorn:

Different operating systems do things differently, and each has to be learned.  It ain't rocket science, but it is non-intuitive, and requires some effort to learn.  With Ubuntu, it's worth the effort, though.

---

### Post by Texas2009 on 2009-03-24
> **sgosnell said:**
> Yes, give her a break.  She apparently went to UT, and is thus severely handicapped.  If she had gone to one of the better universities in the state, she might be more informed.  :p  :tongue:  :D   :popcorn:

Different operating systems do things differently, and each has to be learned.  It ain't rocket science, but it is non-intuitive, and requires some effort to learn.  With Ubuntu, it's worth the effort, though.

HAHAHA! Hey man, I went to a private school close to UT.  I do agree with you about the Longhorns, though!

---

### Post by linuxisevolution on 2009-03-24
> **Texas2009 said:**
> I am brand spankin' new to Ubuntu.  I've used Windows my entire life and I'm starting to regret trying something new.  Ubuntu is Greek to me. Some of the simpliest activities have turned into a hair pulling exercises!  I used openoffice.org to type up a document and I have no idea how to save it directly onto a flash drive. I resorted to saving it directly to the computer and cutting and pasting into my flash drive.  There has to be an easier way.  Help! I'm so used to clicking file - save as - and then simply clicking the drive.  Also, is there an equivalent to "ctrl Alt Delete" when your computer is frozen?


To save to flash drive:

When you click file >> save as there will be a side panel labeled "filesystem - home - picutes - and more...." On that side window will be something that says "1gb media" or whatever size your flashy is. If it's 8gb, it should say "8gb media" and you just click that and click save. THe drive might be named by manufacturer or model also. It's very very simple. 

ctrl_alt_delete= nothing. not needed. When Linux crashes - fully - the caps lock light and the scroll lock lights on your keyboard will light. 
If you want to end a misbehaving program, right click your top or bottom panel, click add to panel, and click "Force quit". Now you can click the force click  button and click whatever program is not working correctly and it will close.

There is one key combo that might be usefull. ctrl+alt+backspace will restart your X session on Linux. Linux is just the kernel, the code, the base bare bones of the cow. What you see (the fur or what do they call it on a cow? lol) would be something literally called X. And while it is running it is called your "X session". ctrl+alt+backspace will restart your x session including any gui applications and return you to the login.

Good luck ;)

---

