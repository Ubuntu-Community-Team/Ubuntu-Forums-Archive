---
title: "Broke 1 TB external hard drive"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by jakupl on 2008-12-24
First of all. Happy Christmas everyone.

I tried to encrypt my 1 TB usb hard disc "MyBook", with TrueCrypt, witch includes formatting it to ext3.
Well when i realized that it would take 42 hours, i aborted, and broke it.

Now my beautiful hard disc wont show up in /media or anywhere.
I guess I need to reformat it, but how do I do that if it wont show up anywhere?

Thanks in advance.

---

### Post by abn91c on 2008-12-24
do you have a windows PC around and try from there?

---

### Post by nynoah on 2008-12-24
you might need to reformat it completely.  Does it show up at all with Gparted?

---

### Post by jakupl on 2008-12-24
> **abn91c said:**
> do you have a windows PC around and try from there?

Yes, I do and it wants me to format it to NTFS and gives me no feedback of anything when I start. So I really don't like it.

---

### Post by jakupl on 2008-12-24
> **nynoah said:**
> you might need to reformat it completely.  Does it show up at all with Gparted?

Yes.

No.

---

### Post by nynoah on 2008-12-24
gparted does not show it all?  Have you tried the Gparted LIVE cd.  You can get that from the net.

---

### Post by nynoah on 2008-12-24
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

Try that.  I know when I had a hard time dealing with some partition issues in the past Gparted LIVE would access and fix them better than doing it through Ubuntu.  Just be careful not to mess with your normal Ubuntu install.  Because Gparted LIVE will do anything you ask it to do, right or wrong.  So just make sure you are messing with the correct disk.  Or if you want to feel safe totally disconnect all the other drives.

---

### Post by jakupl on 2008-12-24
> **nynoah said:**
> gparted does not show it all?  Have you tried the Gparted LIVE cd.  You can get that from the net.

eerh, I'm currently abroad, and I did not bring my gparted live cd. I can try with an Ubuntu live cd. 2 sec.

---

### Post by nynoah on 2008-12-24
No way you can not just redownload it and reburn it?  Gparted can also be run off a flash stick too.

---

### Post by jakupl on 2008-12-24
> **nynoah said:**
> No way you can not just redownload it and reburn it?  Gparted can also be run off a flash stick too.

Yeah, I just changed my mind. I am downloading it. 15 min. to go. Jesus my dads internet sucks.

---

### Post by albinootje on 2008-12-24
> **jakupl said:**
> eerh, I'm currently abroad, and I did not bring my gparted live cd. I can try with an Ubuntu live cd. 2 sec.

You can use gparted from the Ubuntu cd.
If it's not installed, you can install and run it just for the duration of the "live session" from a terminal :
```

sudo apt-get install gparted
sudo gparted

```

---

### Post by nynoah on 2008-12-24
Yeah going from highspeed to slow really sucks............god I can't wait for the day when a T1 line would be a "normal" thing in a house.  Not that I have one.  But someday I am sure everyone will have one.

---

### Post by nynoah on 2008-12-24
> **albinootje said:**
> You can use gparted from the Ubuntu cd.
If it's not installed, you can install and run it just for the duration of the "live session" from a terminal :
```

sudo apt-get install gparted
sudo gparted

```

I have found that in some situations just using the normal install of Gparted in Ubuntu will not always work.  For some reasons with some tricky situations, the Gparted LIVE cd will work and the normal Ubuntu install will not.  Not sure of the reasons why.  But it has been my solution to some issues.  Like one time in the past the install kept on making more partitions rather than wiping out the whole disk for a fresh install.  Gparted LIVE was the only way I could get past that glitch.  Might be the same situation with him now.

---

### Post by nhasian on 2008-12-24
42 hours?  I think thats a high estimate.  It does take a long time but my 1 TB Western Digital Mybook took about 12 hours to encrypt with truecrypt & format as NTFS.  

> **jakupl said:**
> Well when i realized that it would take 42 hours, i aborted, and broke it.

---

### Post by albinootje on 2008-12-24
> **nynoah said:**
> I have found that in some situations just using the normal install of Gparted in Ubuntu will not always work.  For some reasons with some tricky situations, the Gparted LIVE cd will work and the normal Ubuntu install will not.  Not sure of the reasons why.  But it has been my solution to some issues.  Like one time in the past the install kept on making more partitions rather than wiping out the whole disk for a fresh install.  Gparted LIVE was the only way I could get past that glitch.  Might be the same situation with him now.

Thanks for the information! Good to know this.
My idea was to save the OP those 15 minutes of downloading and then burning the cdrom :)

---

### Post by nynoah on 2008-12-24
No worries albinootje............ just explaining my line of thinking.  Not sure if it is the right path.  But maybe someone can learn from my line of thinking.  :)

---

### Post by jakupl on 2008-12-24
So there. The gparted Live does not show anything. Sorry.

What should I do? should I let windows make it NTFS and change it later? how long will it take?

---

### Post by jakupl on 2008-12-24
oh... now not even Windows is recognizing it... aarh.

---

### Post by nynoah on 2008-12-24
WOW huh...........well try redoing it to NTFS in windows and the reformat it later.  That is really odd that it will not even show it at all.  If it does not show in windows, I am wondering if you have a physical drive problem

---

### Post by jakupl on 2008-12-24
> **nynoah said:**
> WOW huh...........well try redoing it to NTFS in windows and the reformat it later.  That is really odd that it will not even show it at all.  If it does not show in windows, I am wondering if you have a physical drive problem

Would that not be a bit strange? The hard disk worked before I reformatted, but after I did it, it was toast. That does not sound very physical to me...

---

### Post by nynoah on 2008-12-24
True it does not sound like it should be a physical problem.  But it IS a possibility.  I just find it very strange that it can not be seen by, windows, Ubuntu, or Gparted.

---

### Post by jakupl on 2008-12-24
Wait, I have two 1 TB Mybooks and I noticed that the malfunctioning one was on all the time, shining with the diode, while the other was off. Neither were connected to a computer and both to a power source. So I restarted the malfunctioning one and connected it to a windows computer. It shows up :)
Now I am reformatting it to stupid NTFS.
I'll keep you updated.
However. This is not why it didn't show up in ubuntu. I tried completely restarting and everything.

---

