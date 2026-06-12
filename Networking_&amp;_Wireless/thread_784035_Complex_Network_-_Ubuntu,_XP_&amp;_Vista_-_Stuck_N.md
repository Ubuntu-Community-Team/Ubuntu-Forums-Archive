---
title: "Complex Network - Ubuntu, XP &amp; Vista - Stuck Newbie"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by fidgaf on 2008-05-06
I am very new to Ubuntu.

I am much happier with Ubuntu and seem to be making good progress (I've even managed to edit my menu.lst)

Ubuntu found my Internet connection without me doing anything but I have other computers that I want to share files with and I'm not being very successful.

What I have:

**Main Desktop**
[LIST]
[*]Duel boot XP Pro and Ubuntu
[*]Wired connection to Orange Wireless Broadband box
[/LIST]

**Second Desktop**
[LIST]
[*]XP Pro only
[*]Ethernet wire to Main desktop
[*]Shares Internet connection with Main Desktop when Main Desktop is in XP
[*]No connection when Main Desktop in Ubuntu
[/LIST]

**Main Laptop**
[LIST]
[*]Vista Home Premium only
[*]Wireless connection to Orange Wireless Broadband box
[*]Public files can be seen on Main Desktop running XP
[*]No connection when Main Desktop in Ubuntu
[/LIST]

**Second Laptop**
[LIST]
[*]Vista Home Basic
[*]Wireless connection to Orange Wireless Broadband box
[*]Public files can be seen on Main Descktop running XP
[*]No connection when Main Desktop in Ubuntu
[/LIST]

[PHP]
2nd PC----(wire)---Main PC
                      |
                    (wire)
                      |
                Orange Broadband
               /                \
        (wireless)            (wireless)
             /                    \
         Main Laptop           2nd Laptop

[/PHP]

All public/shared files can be seen when running XP and Vista.

I can see the Main Laptop, but no files/folders when running Ubuntu.

2nd PC and 2nd Laptop are invisible in Ubuntu.

Is this hopeless or can someone help me make this network usable with Ubuntu running from my main PC.

I hope all is clear.

Thanks.

---

### Post by pro003 on 2008-05-06
did you install samba client for windows network?

to do that right click on some folder in your home directory and select sharing options, than you'll be asked to install support for such protocol... after that try to add these places in xp on the other machine:
 
i.e. //UBUNTU/home/urname/foldernameyouhaveshared

but this is only a part of this whole samba sharing 'story'...

---

### Post by fidgaf on 2008-05-06
> **pro003 said:**
> did you install samba client for windows network?

No.

I have just installed Samba and will see how I do with it.

Tips happily received :)

.

---

### Post by fidgaf on 2008-05-06
Oh Dear ... Not going well :(

I seem to have opened a whole new can of worms.

I went to Find/Remove and found Samba, clicked for it to install, it did and then it crashed when I tried to run it. (Flashy thing in toolbar)

Uninstalled it from Find/Remove.

Went to Samba website, rather confusing for a newbie but pressed on.

Used terminal window to see if samba was there. It wasn't but told me how to install it (*sudo apt-get install samba smbdfs* if I remember right). Script ran and seemed happy.

*smbd -V* tells me I now have *Version 3.0.28a*

Thinking the Samba I got from Find/Remove needed files that I have just installed I tried to install Samba from Find/Remove again. All went well until I ran the program and it crashed again so uninstalled it (still has the bits in the terminal window - see above).

Saw *samba-latest.tar.gz* which opened in *Archive Manager* giving me lots of files I can see but haven't a clue what to do with them and README files don't open from there, apparently.

Thought I would save the file instead (assuming tar.gz is hiding in a buffer somewhere) and it's sitting there grinning. :) Right click doesn't give me an install option.

I hope this is clear again.

I really don't want to have to re-boot into XP to do file transfers on the network.

Long-term (when I have some idea what I'm doing) I want to scrap XP and Vista.




ETA: Did the share thing suggested. Can see the folder on the laptop but can't get in. Allowing guest access means I can see files but can't open them (access is set to me in file properties).

---

### Post by fidgaf on 2008-05-06
Well all seems OK.

I'm a bit puzzled by the failure of the installation from Find/Remove of something called Samba but the stuff visible from the terminal must work OK.

Followed the tutorial I found here:

[http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html](http://www.watchingthenet.com/enable-file-sharing-in-ubuntu-using-samba.html)

a bit dated but works.

I can now see files on the XP machines and even share the Ubuntu printer.

Yay!

Thanks for the help. I would never have got so far without it.

---

