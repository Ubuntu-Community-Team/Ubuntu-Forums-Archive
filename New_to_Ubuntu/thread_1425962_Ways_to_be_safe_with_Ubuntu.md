---
title: "Ways to be safe with Ubuntu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by oingk on 2010-03-09
Hi

I went from windows+ubuntu dual boot to Ubuntu only. This was yesterday. Today, there was a problem created where it wouldn't let me log in. I asked here from the afternoon, but noone showed up that could help me. I didn't know what to do and I needed the computer so I had to reinstall.

Now I am worried that at any time unexpectably some problem might show up that renders my OS unopperatable. Is there a way to avoid this?

A way I can think of is to dedicate a small hard-drive space to windows XP again, where I can go if Linux doesn't work.

What other ways are there?

When I was Windows-only I had a small partition that was dedicated to backing up my system with the help of a special program. Is there such a method possible for Ubuntu?

---

### Post by nothingspecial on 2010-03-09
What was your problem, I didn`t see it.

And yes, there are many backup solutions available on linux.

Have a look at rsync to start with.

---

### Post by 3rdalbum on 2010-03-09
The Ubuntu live CD has always been my backup if things went wrong.

---

### Post by oingk on 2010-03-09
My past problem is here:
[http://ubuntuforums.org/showthread.php?t=1425644](http://ubuntuforums.org/showthread.php?t=1425644)

But nevermind now.

What is rsync?

About the liveCD, fair enough but I'm also worried for the times that I don't have it with me, as I travel a lot.

---

### Post by nothingspecial on 2010-03-09
I don`t know how to fix an encrypted ubuntu, but I have seen the problems.

Do you need ubuntu to be encrypted?

Or do you just need certain stuff to be private?

Or do you just want a working computer?

---

### Post by oingk on 2010-03-09
No. I'm not very experienced with Ubuntu and during installation what I thought it asked me was if I want to password-protect my home folder. I thought why not, but it made things too complex, apparently. When I reinstalled today, I chose "no" when it asked me that question.

So I don't want to encrypt anything.
Now I want to be able to make a back-up thing in some way. So that if things go wrong again, I can restore a previous state of my Ubuntu and not having to lose everything by reinstalling.

---

### Post by nothingspecial on 2010-03-09
There are quite a lot of ways you can back up ubuntu.

What I`m trying to work out, is, is your ubuntu fine as it is.

---

### Post by oingk on 2010-03-09
Yes, I think so.

As I said, I fully reinstalled it today (didn't know what else to do).

Right now, I'm just looking for a way I can backup so that in the future if there is a problem I don't have to reinstall again.

---

### Post by whoop on 2010-03-09
> **oingk said:**
> My past problem is here:
[http://ubuntuforums.org/showthread.php?t=1425644](http://ubuntuforums.org/showthread.php?t=1425644)

But nevermind now.

What is rsync?

About the liveCD, fair enough but I'm also worried for the times that I don't have it with me, as I travel a lot.

Something like this would of probably (well at least possibly) fixed your problem...
```

sudo bash
chown -R user:user /home/user
chmod 644 /home/user/.dmrc
chmod 644 /home/user/.ICEauthority

```

Whenever you get into problem do a bit of googling. Searching for "Could not update ICEauthority file .ICEauthority" would have probably provided you with all the answers you needed.
Please don't take this as criticism, it is just intended as a piece of advise.

---

### Post by halitech on 2010-03-09
IMHO, backing up just your data is less hassle and less work then backing up a complete system as you will need to make new backups everytime an update is done. If you have a seperate /home partition then reinstalling is easy. You can also use Synaptic to mark all installed packages and generate a list tha tyou can use to reinstall apps after a reinstall.

---

### Post by nothingspecial on 2010-03-09
Have a backup, on external media, of any data you don`t want to lose.

Make a seperate /home partition.

Job done.

---

### Post by zeroseven0183 on 2010-03-09
Hi! I think it would be good also to have a separate partition where you store your "good/working disk image". Before, I used to create an updated disk image of Windows XP using [Acronis True Image]("http://www.acronis.com") so that every time my Windows machine crashes, I have this working image ready to be restored.

For Ubuntu, I suggest you use PartImage. The instructions are available at [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage). You can download it using ```
sudo apt-get install partimage
```

---

### Post by oingk on 2010-03-09
OK when I was using Windows and had a problem I could Google and fix in 5 mins, but when I Googled this problem I found some answers but didn't understand a word they were saying. Because I still don't understand easily in regards to Linux. Also, I didn't know if I can trust answers that I find around the web because here in the forums there is a warning by some of the admins that some people post things to make your computer brake as a prank.

So I thought maybe I should better post the question in these forums and judge if the received answers are good by observing how many of you would agree with the answer.

But unfortunately no one at the moment would answer, maybe all of you were working or sleeping or something. Nevermind.

---

### Post by zeroseven0183 on 2010-03-09
By the way, you can also use some online backup solutions for backing up your home folder like [Ubuntu One]("http://one.ubuntu.com") and [Dropbox]("http://www.dropbox.com").

---

### Post by mkvnmtr on 2010-03-09
To me it really helps to have your home on a seperate partition. That way is you are unable to fix something you can reinstall and use the same home and lose nothing but a few apps that you can reinstall. 
Until you feel that you can fix a problem without having a system to google on it is an advantage to have a dual boot.

---

### Post by oingk on 2010-03-09
OK I will check out PartImage.

Regarding creating a separate  /home partition, this seems like a good idea. In this case would I be saving images of my system, or just my files?

Can you give me a good link to info regarding this matter (of creating a separate partition and using it for backing up)?

---

### Post by nothingspecial on 2010-03-09
A seperate home partition is safer.
[[COLOR="Magenta"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by oingk on 2010-03-09
well ok thanks ;)

---

### Post by nothingspecial on 2010-03-09
> **oingk said:**
> OK when I was using Windows and had a problem I could Google and fix in 5 mins, but when I Googled this problem I found some answers but didn't understand a word they were saying. Because I still don't understand easily in regards to Linux. Also, I didn't know if I can trust answers that I find around the web because here in the forums there is a warning by some of the admins that some people post things to make your computer brake as a prank.

So I thought maybe I should better post the question in these forums and judge if the received answers are good by observing how many of you would agree with the answer.

But unfortunately no one at the moment would answer, maybe all of you were working or sleeping or something. Nevermind.

Do not worry too much about this.

Most people here are helpfull

If you are unsure, ask for confirmation.

I can assure that this problem has been dealt with. I haven`t seen it in over 3 years.

---

### Post by nothingspecial on 2010-03-09
Having read my last post again......

Yes..... Do worry about it, a little

The basic rule is - don`t put anything in the terminal unless you know what it does.

---

