---
title: "Crazy login"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-11-15
I've just installed Lubuntu on my wifes old rubbish desktop. I can log in via command line, but not the normal login screen, it just keeps asking for username, then password, then username...password ad infinitum. So whats that all about?

Will probably reinstall it and try again, and was thinking about using the PC as a file server anyway, just wanted to see how well Lubuntu would run on it first.

---

### Post by toekneewood on 2010-11-15
old rubbish desktop  :(   How about giving it a fighting change and putting it on a GOOD desktop.  You will get a better experience.  When you are at the GUI does it show the list of available users?  Don't forget that the username and password (+files and directory 's) in Linux/Unix is case sensitive

Beans: 1,151 did you mean to post this one in the **Absolute Beginner Talk?**

---

### Post by migs73 on 2010-11-15
> **toekneewood said:**
> 
Beans: 1,151 did you mean to post this one in the **Absolute Beginner Talk?**

Read his signature!!!!

I feel much the same! :)

---

### Post by amjjawad on 2010-11-15
What's your system specifications?

---

### Post by Hippytaff on 2010-11-15
> 
Beans: 1,151 did you mean to post this one in the [B]Absolute Beginner Talk?

[/B]It is a beginnerish question, though I forgot to check which one I was in before I posted.

I wanted to see if the pc could cope with Lubuntu, I'm sure it can, just this little hurdle :-)

-no list of users and the user/password is correct.

Startx doesn't work either.

---

### Post by toekneewood on 2010-11-15
> **migs73 said:**
> Read his signature!!!!

I feel much the same! :)
I did, that is why I have asked.  I have been using linux for about 5years at home and work.  I have only just started to spend some of my lunch breaks and evenings trying to help out people that run into problems.  I think that I was expecting people with about 1000+ beans would be very experienced.  Still learning the way around the forum, looks like i have still got some learning to do when it comes to reading between the lines.

---

### Post by sandyd on 2010-11-15
> **Hippytaff said:**
> [/B]It is a beginnerish question, though I forgot to check which one I was in before I posted.

I wanted to see if the pc could cope with Lubuntu, I'm sure it can, just this little hurdle :-)

-no list of users and the user/password is correct.

Startx doesn't work either.

press CTRL+F1
login with your user account.

check output of .xsession-errors
```

cat ~/.xsession-errors
```
and I need to remove my birthday sig.....

---

### Post by toekneewood on 2010-11-15
How about 
```

lspci

```
Looks for your video driver and then look in   [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)  to see if it is on the supported list __

---

### Post by Hippytaff on 2010-11-15
I've only been using Linux for 6 months, steep learning curve, but I'm not doing too bad. But The sig is there for a reason :-) mostly stupid questions :-) though I help out where I can.

Perhaps the mods will move it to General :-s

---

### Post by migs73 on 2010-11-15
By his signature I meant this; "Don't be fooled by the number of beans I have. They are mostly stupid questions"

Although I think he is doing himself a bit of disservice there, I could say that of my 555 (it'll be 556 now!) probably 55 merit beans!!!

Don't tell the Mods!  :lol:

---

### Post by toekneewood on 2010-11-15
I have just spotted this comment on the website below, so not sure if they have the same list of drivers in this build  "The lubuntu team aims to earn official endorsement from Canonical"

[http://lubuntu.net/](http://lubuntu.net/)

Do you think that it would be work trying a live CD version of Ubuntu 10.10 to see if you can get it into the GUI?

---

### Post by Hippytaff on 2010-11-15
> **toekneewood said:**
> How about 
```

lspci

```Looks for your video driver and then look in   [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)  to see if it is on the supported list 

Video driver is supported - 10.10 livecd works ok

no Xsession errors reported, just says started xsession for user - time -

Though there is a massive log in Xorg.0.log file...having a look now (and trying to find my usb stick to post it)

---

### Post by toekneewood on 2010-11-15
just spotted this one  [http://forum.eeeuser.com/viewtopic.php?id=30192](http://forum.eeeuser.com/viewtopic.php?id=30192)

It has the same error "Xsession: unable to start X session --- no"

---

### Post by Hippytaff on 2010-11-15
Thanks toekenwood, appreciate that, helps me narrow down the possiblities :-)

the only thing in the log that looks like it might be helpful is
```

Open ACPI failed {path to file} file does not exist

```
to paraphrase slightly

---

### Post by Hippytaff on 2010-11-17
Sorted it...in case anyone wants to know how :-)

I removed and reinstalled lxde.

---

