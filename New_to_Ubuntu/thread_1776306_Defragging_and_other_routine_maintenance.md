---
title: "Defragging and other routine maintenance?"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by RotorRick on 2011-06-05
Defragging and other routine maintenance?
 

 I've been using ubuntu 10.04LTS for about four months now, and I need to ask: is there any sort of regular routine maintenance I should schedule? In Windows for instance, it's highly recommended to run a Defrag routine every now and then, along with some other items, like emptying cookies and whatnot. Do I need to concern myself with similar things, and if so, what exactly?

---

### Post by papibe on 2011-06-05
I wouldn't worry about fragmentation, because the system is designed to avoid fragmentation in disks. Read more [here ]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting")is you're interested.

Regards.

---

### Post by |{urse on 2011-06-05
Not really, just make sure your system is relatively free of dust and test your ram occasionally with memtest (on the livecd). Ain't Linux grand?

---

### Post by garvinrick4 on 2011-06-05
> p { margin-bottom: 0.21cm; }Edit your post and delete this part.

## No about every 20 or so boots Ubuntu linux runs a fsck that is all it needs.
Can run with live cd (ubuntu install cd using Try Ubuntu) run "sudo e2fsck /dev/sd[COLOR=Red]xy[/COLOR]"
in a terminal without quotes.
x=drive
y=partition number
First drive in order is sda second drive is sdb third drive is sdc and so on and on.
first partion number is 1 second is 2 third is 3 and so on and on.
##Cannot run fsck on a disk that is mounted is why you need a live cd or another install of linux.
> like emptying cookies and whatnot.In edit and preferences of firefox you can delete cookies if you choose, will lose all your
passwords you have set as remember. Do what you like.

---

### Post by wildmanne39 on 2011-06-05
> **RotorRick said:**
> p { margin-bottom: 0.21cm; }  Defragging and other routine maintenance?
 

 I've been using ubuntu 10.04LTS for about four months now, and I need to ask: is there any sort of regular routine maintenance I should schedule? In Windows for instance, it's highly recommended to run a Defrag routine every now and then, along with some other items, like emptying cookies and whatnot. Do I need to concern myself with similar things, and if so, what exactly?

Hi, it is always a good Idea to set your browser to delete cookies after a few days, so they do not slow down your system,I have mine sit to delete every 2 days. As for the rest there is no need for defrag or anything like that, your hard disk should be set to check its self every 30 boot ups, so it is all a nonissue.

---

### Post by Drate on 2011-06-05
Short answer: No.  No need to mess with defragging or other similar maintenance.  Quasi-explanation below:

Celebrate the end of the defrag.  The filesystems used by most GNU/Linux systems were originally designed for multi user environments.  We're talking way back, when you had dummy terminals that just connected you to a central server, and everybody was accessing their account at the same time.  Thus, the filesystem had to be accessing different portions of the hard drive all the time, and by design have no need for defragging, which (for the sake of this discussion) just makes the whole filesystem one contiguous chunk of information.

Now having said all that, there is one thing you can do if you find you are running dreadfully low on diskspace:

```
sudo apt-get clean
```

Everytime you install something, it downloads a file, maybe several, and then keeps them in case you want to uninstall and reinstall for some reason.  Running "apt-get clean" will clear those installer files out.  Now I'm not sure how long they are kept or if Ubuntu auto-cleans them at some point, and honestly I've never really NEEDED to run the "apt-get clean" command.  Unless you have a tiny tiny hard drive, or install WAY MORE STUFF than what you would likely be using, you'll probably be fine just letting it ride.

---

### Post by Timmer1240 on 2011-06-05
I use BleachBit it gets rid of all the junk files old log files catche and cookies ect off the system

---

### Post by athenroy on 2011-06-05
You might check out Bleach Bit.  Sorry, I don't have there URL handy.

---

### Post by oldsoundguy on 2011-06-05
I use this occasionally to remove left over files (Yes, Linux DOES leave some crud behind .. but NOT the gigabytes that Windows leaves that slow the thing down!)
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

It has some strong utilities, also.  But do NOT do anything that you may have some doubt about what will happen.  (IE .. leave the kernel accumulation alone!!!!! You can ask for help here on the forum and someone will tell you what to KEEP.)

---

### Post by Irihapeti on 2011-06-06
[Backing up]("https://help.ubuntu.com/community/BackupYourSystem") is always a good idea.

---

