---
title: "sync my blackberry"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Jaimie Dunford on 2010-07-27
Hi Everybody,

I might sound a bit thick (well I probably am) but I would like to know how to do a couple of things on ubuntu.
I have to admit that when looking at previous threads the language used may as well be Martian to me, I really can't make head or tail of some of it, so I thought I would ask you guys if you could explain it as if you were explaining it to someone who has never seen a computer before.

I would like to be able to sync my blackberry 8250 with "evolution"  and also to sync my ipod to this system. I have ubuntu 10.4 I kind of gather something about "barry" is some kind of hybrid programme to enable the blackberry sync, however when I went to the web page there was no download; at least not any in a format I am familiar with (i.e. download - press enter!!!) and consequently got terribly lost in it all.

How do I download the programmes to enable those items to work on Ubuntu; and also; how do you get rid of cookies etc that must build up when surfing the web?

Apart from the fact that I am somewhat embarrassed at my computing skills  (or lack of) I think Ubuntu is really quite superb, far better than Vista which i had been using.


Any help you may be able to give me will be very much appreciated.

Kindest regards,


Jaimie Dunford:confused:

---

### Post by Goolie on 2010-07-27
I'm not familiar with blackberries, but this seems like a pretty good walk-thre on installing Barry.

[http://netdirect.ca/software/packages/barry/install.php](http://netdirect.ca/software/packages/barry/install.php)

and syncing your blackberry with evolution.

[http://netdirect.ca/software/packages/barry/sync.php](http://netdirect.ca/software/packages/barry/sync.php)

And, glad you like Ubuntu.

And your cookies can be deleted from within the browser your using most likely, how, depends on what browser your using.

---

### Post by Res2216firestar on 2010-07-27
Applications>Ubuntu software center. I believe the app you are looking for is "opensync-plugin-barry". Pasting that into the search box and hitting install should do the trick. iPods should be plug-and-play with Rhythmbox (Applications>Sound and Video). Clearing your cookies is Tools>Clear recent history is firefox, or Ctrl+Shift+Del. Welcome to Ubuntu :)

---

### Post by Jaimie Dunford on 2010-07-27
Thank you guys, that has helped enormously; I was getting dizzy where I was going round and round not getting anywhere.

Thank you:D

---

### Post by linux18 on 2010-07-27
Sometimes when you look in other threads, you see the unashamed ultra-geeky posts with our "Martian" code:
```
sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"
```by the way, copy/pasted one line at a time into a terminal, this cleans and updates synaptic

but everyone who sticks to linux will soon be posting their own codes and in time you too will probably understand the meaning of ```
pd() { for i in $(find $@) ;do pdftohtml -stdout -i -noframes -nodrm $i > $i.htm && links $i.htm ;printf "any key: continue\nq: exit to shell\n" ;read j ;case $j in q) rm $i.htm ;break ;esac ;done ;} usage: pd <file glob>
```with linux you learn about computers and computing, with windows you learn about viruses and bloated software. Best of all, theres no pressure if you think you have to learn anything your wrong, you can be a noob forever. theres no pressure to learn linux and you can go back to windows anytime, no hard feelings, were all about freedom here.But were pretty sure you'll like it!

---

### Post by Jaimie Dunford on 2010-07-28
Thank you guys, I am sure I will get it one day, if not I'll have fun trying; 

thank you.

J.

---

### Post by Jaimie Dunford on 2010-07-28
Hi guys.

Still got problems, downloaded barry, it's on my pc; plugged in my blackberry - nothing; what am I doing wrong??:(:confused:

Cheers guys.

J

---

### Post by llamabr on 2010-07-28
How did you "download" barry?

Try this from the terminal:

```
sudo apt-get install barrybackup-gui
```

---

### Post by Jaimie Dunford on 2010-07-28
Thanks for that, it seemed to download, but when I plug in the bb -nothing! look all over the pc and nothing, don't know where to look now:(

off to bed now but if you have any further ideas, I would be grateful to hear them; cheers.

J.

---

### Post by llamabr on 2010-07-28
[http://ubuntuforums.org/showthread.php?p=9276901](http://ubuntuforums.org/showthread.php?p=9276901)

---

### Post by Jaimie Dunford on 2010-07-29
Hi llamabr, used that link got to : index of modules/blackberry/ubuntu, now do I download the 364 kb version; and if so what should that do ?
 
J.
** **

---

