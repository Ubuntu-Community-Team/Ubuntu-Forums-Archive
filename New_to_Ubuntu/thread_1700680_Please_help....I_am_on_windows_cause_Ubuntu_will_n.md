---
title: "Please help....I am on windows cause Ubuntu will not let me in"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Amber2011 on 2011-03-05
I disabled the Ubuntu sign in screen and all was well with that. Today I turned on my computer and that sign in screen was back. But it will not sign me in, I tried many times, I tried shutting down the computer, nothing helps. What can I do? I mean I can't even get into the terminal this way......or wherever I need to go to fix this. Thanks

---

### Post by maqtanim on 2011-03-05
Check out whether the capslock is on or off?

---

### Post by Amber2011 on 2011-03-05
No the caps are fine.

---

### Post by quesadilla on 2011-03-05
numlock (if you have it on your keyboard) could also be on... that messed me up once when I couldn't log in

---

### Post by Amber2011 on 2011-03-05
No I use mini keyboards I do not have that feature. I knew when I seen that sign in-screen after I disabled it I was in trouble.

---

### Post by vivek.pandey on 2011-03-05
> **Amber2011 said:**
> I disabled the Ubuntu sign in screen and all was well with that. Today I turned on my computer and that sign in screen was back. But it will not sign me in, I tried many times, I tried shutting down the computer, nothing helps. What can I do? I mean I can't even get into the terminal this way......or wherever I need to go to fix this. Thanks

do you mean here that you cant shut down your system or even after shutting you cant fix it? if you can shut it down 
restart your computer and press delete you will get the grub... you can then login through console

---

### Post by Mark Phelps on 2011-03-05
I don't think it's the Del key; I think it's the SHIFT key -- to force the GRUB menu display.

---

### Post by Amber2011 on 2011-03-05
I must be losing my mind or something, I posted this already but I can't find it. I am having a badddd computer day. Youtube videos will not play, I tried them on 3 browsers. But my main deal now is Ubuntu will not let me in. I disabled the sign-in page and that was fine till today. I turned on computer and when it connected to the Ubuntu desktop the sign-in page all of a sudden was there. Somehow I knew I was in trouble. It will not let me in matter what I do. I restarted, typed my password  2 dozed times. Without that I can't get into the area to work on a problem. My caps are not on, just to rule that out. Any ideas?

---

### Post by vivek.pandey on 2011-03-05
i guess you posted a similar problem in absolute beginners section ..there are some replies..check them out there

---

### Post by sikander3786 on 2011-03-05
You can reset your password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

For Youtube issues, you can try using the flash-aid add-on which will remove any conflicting plugins and install the appropriate one.

[https://addons.mozilla.org/sl/firefox/addon/flash-aid/](https://addons.mozilla.org/sl/firefox/addon/flash-aid/)

---

### Post by overdrank on 2011-03-05
Threads merged :)

---

### Post by Amber2011 on 2011-03-05
> **sikander3786 said:**
> You can reset your password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

For Youtube issues, you can try using the flash-aid add-on which will remove any conflicting plugins and install the appropriate one.

[https://addons.mozilla.org/sl/firefox/addon/flash-aid/](https://addons.mozilla.org/sl/firefox/addon/flash-aid/)

Please ignore any goofs or duplicates or anything, I have been at computer problems all day and I can't think clearly now.

Anyway I got to the root shell page and basally I get messages like : no such file or directory found (when I type in password or that ls/home). I don't know I am so mad now. I think I will go out for a coffee and check back later. I may have to uninstall this. Though I want to work more in the page you told me about, just do not know what else to do. Thank you and everybody.

---

### Post by vivek.pandey on 2011-03-05
if you are getting console ..type startx and you will get a gui

---

### Post by lisati on 2011-03-05
> **Amber2011 said:**
> Please ignore any goofs or duplicates or anything, I have been at computer problems all day and I can't think clearly now.

Anyway I got to the root shell page and basally I get messages like : no such file or directory found (when I type in password or that ls/home). I don't know I am so mad now. I think I will go out for a coffee and check back later. I may have to uninstall this. Though I want to work more in the page you told me about, just do not know what else to do. Thank you and everybody.
[LIST]
[*]See [http://www.computerhope.com/unix/upasswor.htm](http://www.computerhope.com/unix/upasswor.htm) for information on setting your password from the command line
[*]Try **ls /home** (with a space in it)
[/LIST]

---

### Post by Amber2011 on 2011-03-05
overdrank,
I know they merged that is what I meant when I apologized for anything goofy, lol when I started seeing my post all wacked out I knew it was time for a break.

neo_aryan,
I will try that

lisati,
thanks I will check that out too. I did try the ls/home but I do not believe I put a space in it.

Thanks for everybody's help, I have a few things to try now. I really appreciate it.

---

### Post by Amber2011 on 2011-03-05
Hey everyone,

I got it!!!!!! The "startx" thing worked. I also got my Youtube videos working. The only issue is Ubuntu did not save anything, so I need to download things and set my mail back up and all that but I only had this about a week so not much of a problem. One thing for sure this is how you learn!!!

You have not idea how much I appreciate you guys helping us newbies out. Thank you all very much who helped.

---

### Post by sikander3786 on 2011-03-06
> **Amber2011 said:**
> Hey everyone,

I got it!!!!!! The "startx" thing worked. I also got my Youtube videos working. The only issue is Ubuntu did not save anything, so I need to download things and set my mail back up and all that but I only had this about a week so not much of a problem. One thing for sure this is how you learn!!!

You have not idea how much I appreciate you guys helping us newbies out. Thank you all very much who helped.
I think your /home is somehow missing. How, I don't know. In order to know that, we need to see the outputs of these commands.

Was the /home on a separate partition?

```
sudo fdisk -lu
cat /etc/fstab
```

---

