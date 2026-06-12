---
title: "Few Questions!!!"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by Elfyy on 2011-07-15
So, I have a 2007 Gateway laptop that today I installed the newest version of Ubuntu and am dual booting (I'm on windows now!). I have a Intel Pro/Wireless 2200BG card in my laptop, but I use a usb AE1000 due to it being faster since it is newer.  I cannont connect to wireless what so ever on either one(I would perfer the AE100.) I have searched high and low but I cannot find a fix that works...This brings me to my next question, Most of the fixes I see involve going to System-Administrator.  How exactly do you do that? I have no system bar up top like all the video tutorial I see? I would love to keep trying linux but if I can't get these issues sorted out, its back to windows!!!
Thanks a bunch!!

---

### Post by wolfen69 on 2011-07-15
Check *Additional Drivers* in ubuntu to see if there is a wireless driver available. You will need to be plugged in to the net for this.

---

### Post by Elfyy on 2011-07-15
> **wolfen69 said:**
> Check *Additional Drivers* in ubuntu to see if there is a wireless driver available. You will need to be plugged in to the net for this.

Thanks I tried that but it didn't find any...

---

### Post by wolfen69 on 2011-07-15
When buying hardware for linux, you need to make sure it is compatible. Kind of like a Mac.

---

### Post by Elfyy on 2011-07-15
> **wolfen69 said:**
> When buying hardware for linux, you need to make sure it is compatible. Kind of like a Mac.

Thats what it;s beginning to seem like unfortunatly... But then how do you get into the the system-admin?

---

### Post by Elfy on 2011-07-15
In unity which I think perhaps you're using it's in the menu under your username at the top right - at least I think it is there.

---

### Post by Elfyy on 2011-07-15
> **forestpiskie said:**
> In unity which I think perhaps you're using it's in the menu under your username at the top right - at least I think it is there.

Thats systems settings but there is no admin menu in it...

---

### Post by Elfy on 2011-07-15
Oh right ok thanks.

From the short time I used unity I don;t think there is a 'admin menu' - you could try searching for whatever you're looking for in the search thing in the dash

Doesn't take long to forget once you're using a different system.

---

### Post by Swagman on 2011-07-15
Either from the terminal (ctrl + alt + t) or press alt F2 and enter gksudo.. In Unity you will get a list of sudo (admin) choices

or

Click ubuntu logo top left and enter update (it'll find the manager before you complete it)

Try clicking settings (at the bottom) and make sure universe & multiverse are ticked in the first tab and in the "updates tab" proposed & backports is ticked.

r: your wireless network issue have you tried left clicking the network icon top right of your screen ?

---

### Post by dFlyer on 2011-07-15
> **Elfyy said:**
> So, I have a 2007 Gateway laptop that today I installed the newest version of Ubuntu and am dual booting (I'm on windows now!). I have a Intel Pro/Wireless 2200BG card in my laptop, but I use a usb AE1000 due to it being faster since it is newer.  I cannont connect to wireless what so ever on either one(I would perfer the AE100.) I have searched high and low but I cannot find a fix that works...This brings me to my next question, Most of the fixes I see involve going to System-Administrator.  How exactly do you do that? I have no system bar up top like all the video tutorial I see? I would love to keep trying linux but if I can't get these issues sorted out, its back to windows!!!
Thanks a bunch!!

I believe my wife has the same gateway laptop. Everything just seems to work out of the box. I don't know anything about the usb AE100, but I believe to get the on board wifi working, you will need a hardwired network connection and then check for additional drivers.

---

### Post by wildmanne39 on 2011-07-15
Hi, here is a link to get the usb card working, you will have to disable the internal wireless for this to work.
[http://ubuntuforums.org/showthread.php?t=1630358&highlight=usb+AE1000](http://ubuntuforums.org/showthread.php?t=1630358&highlight=usb+AE1000)

Also most of this will be done in a terminal you can open it by hitting ctrl+alt+t.

---

### Post by Elfyy on 2011-07-15
Thanks for the help, I tried everything including the link wild man and I just get errors on the terminal... Do I have to be signed in under root? Thanks!!

---

### Post by Elfyy on 2011-07-15
Ugh.... This is so frusturating, i'm think of just uninstaalling it and going back to windows... would 10.4 be better?

---

### Post by wildmanne39 on 2011-07-15
> **Elfyy said:**
> Ugh.... This is so frusturating, i'm think of just uninstaalling it and going back to windows... would 10.4 be better?
Hi, to run commands in the terminal you type sudo in front of it and then it will ask for your password, please note that you will not see your password as you type it so when you are done you just hit enter.
Here is a link for sudo.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

