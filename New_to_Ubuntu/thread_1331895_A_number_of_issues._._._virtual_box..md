---
title: "A number of issues. . . virtual box."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by profozone on 2009-11-19
So I've really been looking forward to getting into Linux for all of the reasons you all know.  I tried loading it alongside Vista on my Dell laptop, but had trouble due to the partitions.  A friend told me about Virtual Box, so I loaded that onto my laptop and I have to say that seems like a pretty decent piece of software.  Very easy to load with great instructions.  After loading virtual box, I put my Ubuntu Ultimate Edition 2.3 disc into the DVD player and loaded it on, no problem.  But before I even had a chance to use it, an update notice popped up and I said ok.  I then endured a very long download and a long install to 9.10 at the end of which I just got a bunch of permanently flashing text.  I searched for a while on how to solve this problem but just figured I could use the old version for a while as I got used to Linux.  I successfully loaded it back on and it seemed to be working properly, but the virtual box warned that it's color resolution needed to be set to 32 bit(in Ubuntu).  I couldn't find this setting anywhere in Ubuntu.  Plus the screen only occupied a portion of my monitor and I wanted to use it full screen, so I went into display to set it.  The only two options were 800x600 or 600x480.  I also tried to change my cursor from that huge spinning thing to something a little smaller, but the button presses didn't seem to actually do anything when I found the one I wanted from the impressive selection.

Sorry for the long post, but I was wondering if anyone could tell me if these issues have to do with running it on a virtual machine or am I doing something wrong?  There appear to be a whole bunch of cool features in Ubuntu, but I don't seem to be able to select them.  I think the major stuff works.  For instance, I was able to get on the net using Mozilla.

Comments?

Thanks.

---

### Post by benerivo on 2009-11-19
A couple of the things you mention are due to virtualbox. They are the screen resolution problem, and the 32 bit colour warning. The big download for the updates was due to you using the dvd version (ie. the dvd has more programs on it, and therefore there is more to update when new versions of them become available). The cursor thing is usaully solved by logging out and back in again.

What i would suggest is the standard live cd, and trialling ubuntu by installing it from within windows using wubi (which doesn't require partitioning) - see here...
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can solve the full screen problem, and improve the virtualbox experience by installing the virtualbox addons. I think this should be installable from the main menu of the virtualbox window when your virtual ubuntu is running.

---

### Post by profozone on 2009-11-19
Wow!  I expected flames, but you answered pretty much all of the questions.  Thanks a lot.  You rock!

So a follow up question, however.  I figured I could solve the 32 bit thing by just changing the resolution to 32.  Is it possible or is this just a bug?

Thanks again.

---

### Post by holiday on 2009-11-19
He's right. Install the GuestAdditions. It's under the Devices menu. With the latest Ubuntu versions this will perform the installation. 

VirtualBox will play Ubuntu in full screen, full resolution with excellent performance for all but the most demanding apps. You have to help it out a bit at first and the steps of that help will depend on your situation. 

It's a simple utility once you get the hang of it.

---

### Post by profozone on 2009-11-20
Ok, I'm trying to do some of these things now.

To install the Guest Additions, it prompts me to do this as an administrator.  In Windows I would right click and find that as an option.  Couldn't quite figure out how to do it in Linux.

While I'm on that subject, is it possible to give whomever is using the computer administrative privileges?  I have it set up as a single user and I'm not worried about someone stealing the computer.  Although, maybe I should be worried about intrusions via the internet.  Or should I?

Thanks again for the help.

---

### Post by JoeBlow9878 on 2009-11-20
For administrative privileges in Ubuntu, you just have to use your own password (the one you use to log in), provided you are a user with administrative privileges.  This will be the case for the first user created during the install process.  If you install the guest additions from the command line (that's the way I did it in Ubuntu 9.04), simply type "sudo" without quotation marks before the command (ex.: sudo sh autorun.sh). Then type your password when prompted.

To install guest additions from the terminal, here are the instructions: 
1) open the terminal (Applications / Accessories / Terminal)
2) type cd /media/cdrom0
3) press Enter
4) type sudo sh autorun.sh
5) follow the on-screen instructions.

The answer to your second question is yes.  When you set up multiple users, you have the choice as to whether or not they are administrators or not (at least we did in 9.04).

I hope that helps!

Joe

---

### Post by danastasio on 2009-11-20
logging in as root is extremly dangerous and discouraged my many (myself included) if it possible for you to never ever ever use the root account, you should do so.
To run something as root you can use 
```
sudo command
```
in the command line. sudo grants you root permission, but only for 5 minuets, so it is very much safer than the root account. The reason linux is so secure is because you dont have access to any of the files outside of your /home directory. You can't change the root file system willy nilly, and as such, neither can anyone that would try and crack into your system.
However if you login with the root account, and accidentally type (and i have dont this
:rm -rf /: <- NEVER EVER RUN THIS!

it will delete everything that exists on your computer without question
so you can see the obvious security advantages :P

---

### Post by darkksyde on 2009-11-20
All you have to do is install the guest additions, I don't have VBox installed atm but if you poke around in the menus im sure you will find it.

---

### Post by Dennis N on 2009-11-20
Guest Additions are from Devices > Install Guest Additions.

That allows seamless mouse integration between host and the guest OS window as well as full screen mode (Rt-Ctrl + F).

One time-saving suggestion: When you want to quit the VM, you don't need to shut down the guest OS. Leave full screen mode (Rt-Ctrl + F) and then close the VirtualBox window. It will prompt you what to do. If you select "Save Machine State" (top choice) everything (such as open applications) will be restored next time you start the machine - similar to suspend on a laptop. You don't need to go through the boot up and log-in process for the guest OS next time.

---

### Post by profozone on 2009-11-20
Sweet.  Thanks these are great suggestions.  Yet more questions however. . . so does this mean the Joeblow's suggestion should NOT be followed because it uses the sudo command and therefore puts me in as root?

I found the guest additions a while ago and the readme file told me what to do. . . sort of.  It said "do" this and gave me what looked like a command line entry, but I didn't know where to enter it since I was in a GUI.  However, just below that folder was one with the exact name of what was in the command line, so I double clicked on it and it created an .iso file.  Reading the VMbox help, it said to mount and run this from "WITHIN" the window that has linux.  So I did this and it started to load, then stopped and said that I had to run as an administrator.  I don't know how to do that in Linux.  Like I mentioned, I only know how to do this in Windows.

On a possibly related note, I did stumble upon some "authorizations" somewhere on the desktop.  I didn't understand what they all were, but most of them said, 'NO" for authorization.  One of them was for desktop.  Is it possible this is the reason I can not change my ginormous cursor?  Yup, logging out and back in, didn't fix that problem.

Sorry for all the newb questions.  I was reading a book on Ubuntu at Barnes and Noble that was pretty good, but I didn't buy it because it was kind of pricey and I knew there was a lot of support online.  Now I'm starting to think I should have gotten it.  I find books easier to read than surfing around for hours on end.

I'm really looking forward to getting into this.  I love the look and in Windows it seems I already use a lot of the programs like (Open Office, VLC, Mozilla, 7zip or zip7, whatever it's called.)

Thanks for all the help.

---

### Post by benerivo on 2009-11-21
You need root permissions when you want to make system changes. Installing the guest additions package is a system change so you will need to use the sudo command to give you priviliges. If you get the .iso file on your desktop, then you can open a terminal and do```
cd /media/cdrom0
```which just puts the command line in to the guest additions cd folder. Then run the installation script for linux (32bit guest example used below)```
sudo ./VBoxLinuxAdditions-x86.run
```

---

### Post by profozone on 2009-11-21
Have you guys abandoned me?

Have I mentioned how much I appreciate your help?  Maybe I don't say it enough.  You know people often don't say these things enough to the ones that mean a lot to them.  .  . so I hear.

Hello?  Is this thing on?

Thanks. [SIZE=1](sniffle)[/SIZE]

---

### Post by JoeBlow9878 on 2009-12-09
Hello profozone,

Did you ever get this working?  In answer to your question, yes it is OK to use "sudo" in this instance.  As benerivo said, you need root permissions to change system things.  What problems are you having?  If you follow my steps, guest addtions should install correctly.  That is how I did it.  Just use the steps that I gave you in my previous post.

Also, when you use "sudo" in the command line, you are NOT logging in as root.  You are simply enabling you to act as a "root" user for about 5 minutes (if it's the same as it used to be).  And at that you only have those root privileges from the command line.

If you still have issues about "sudo" in the terminal, feel free to write back.  If you are having problems with the code I sent you, please post the errors.

Thank you1

Joe

---

