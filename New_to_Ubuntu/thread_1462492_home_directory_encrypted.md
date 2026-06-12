---
title: "home directory encrypted"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by stroyeror on 2010-04-25
OK i have encrypted my home directory. but when i put a live cd to move the data off i can not access the directory. If i do "sudo nautilus" i am able to see "access your private data" icon and the readme.txt.  when i click on access your private data a windows appears and quickly disappears what is going on here?

---

### Post by wojox on 2010-04-25
That why it's encrypted. It would be kind of silly to encrypt it then let someone boot a Live CD and gain access to everything. :)

---

### Post by stroyeror on 2010-04-25
> **wojox said:**
> That why it's encrypted. It would be kind of silly to encrypt it then let someone boot a Live CD and gain access to everything. :)


Yes I know that the live cd would not allow me to see the files. But shouldn't it ask for a pass phrase in order to mount the Drive?

---

### Post by warfacegod on 2010-04-25
> **wojox said:**
> That why it's encrypted. It would be kind of silly to encrypt it then let someone boot a Live CD and gain access to everything. :)

Couldn't have said it better myself.:P

---

### Post by jflaker on 2010-04-25
> **stroyeror said:**
> OK i have encrypted my home directory. but when i put a live cd to move the data off i can not access the directory. If i do "sudo nautilus" i am able to see "access your private data" icon and the readme.txt.  when i click on access your private data a windows appears and quickly disappears what is going on here?

I think you would need to get encryptfs from the repositories...then you may be able to decrypt the volume with the right passphrase.

Although, I've never done this so I can't speak from experience.

---

### Post by stroyeror on 2010-04-25
> **warfacegod said:**
> Couldn't have said it better myself.:P


You two should learn how to read.....  



to jflaker thanks ill give that a try.

---

### Post by stroyeror on 2010-04-25
ok so I installed ecryptfs and all that pops up is a terminal windows and then it closes. SO tell me since the data is encrypted how does one access it from out side the OS.  I thought it was suppose to ask for a pass phrase.

---

### Post by warfacegod on 2010-04-26
Try: gksudo ecryptfs

---

### Post by Paddy Landau on 2010-04-26
Unfortunately, home encryption is not well implemented except for basic standard use. There is a way to access it from a Live CD, but it's complicated.

Read the following. The first three give you some good background so that you can understand (sort-of) what's going on, but only the fourth one gives you the **correct** answer.

[LIST=1]
[*][https://help.ubuntu.com/9.10/serverguide/C/ecryptfs.html](https://help.ubuntu.com/9.10/serverguide/C/ecryptfs.html)
[*][http://www.linux-mag.com/id/7568/1/](http://www.linux-mag.com/id/7568/1/)
[*][http://ecryptfs.sourceforge.net/README](http://ecryptfs.sourceforge.net/README)
[*][http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)
[/LIST]

---

### Post by Calash on 2010-04-26
> **stroyeror said:**
> Yes I know that the live cd would not allow me to see the files. But shouldn't it ask for a pass phrase in order to mount the Drive?

Unfortunately, or fortunately depending on how you view it, this is not how encryption works.

What you want to do goes against the very reason that you would encrypt data to begin with.  It is designed to prevent accessing data from an external OS.  We use it at work in the event that laptop drives get stolen nobody will be able to just connect it to another system and lift the data.  In our case it requires a token that changes every minute to see the drive in a LiveCD type environment.

I am not familiar with how Ubuntu is implementing the encryption but do not expect it to be easy to get access to the data.  If it is easy then it is not worth encrypting the drive to begin with.

---

### Post by Paddy Landau on 2010-04-26
> **Calash said:**
> If it is easy then it is not worth encrypting the drive to begin with.
I disagree.

I have a safe. It's easy to get into *when I have the correct combination*, but extremely hard to get into when I don't.

Encryption should be the same. Easy to get into when you have the correct passphrase, but extremely hard to get into otherwise.

---

### Post by Calash on 2010-04-26
> **Paddy Landau said:**
> I disagree.

I have a safe. It's easy to get into *when I have the correct combination*, but extremely hard to get into when I don't.

Encryption should be the same. Easy to get into when you have the correct passphrase, but extremely hard to get into otherwise.

The difference is going in the door of the safe, being the functioning operating system, and cutting a hole in the side as a way to bypass a broken door.

---

### Post by Paddy Landau on 2010-04-27
> **Calash said:**
> The difference is going in the door of the safe, being the functioning operating system, and cutting a hole in the side as a way to bypass a broken door.
Yes. Modern encryption methods, *when done properly*, are so secure that in practical terms they are unbreakable. If it contains military state secrets or details of a child pornography ring, a government might spend the money and time to break it, but for the average user, it's not going to be broken.

If you have your passphrase, why prevent you from accessing your data just because you booted from a Live CD and not from the installed OS?

I had this very problem. A friend's computer suffered hard disk corruption, so that the computer could not boot. Fortunately, the data area was still intact; I was able to boot from the Live CD and, with the 32-character unlock key that ecryptfs had provided, I was able to recover the data. But it took me over a month to find the solution!

If the encryption had been designed such that you could decrypt *only* when booting with the installed OS, my friend would have lost everything. And, how would you get into your data when you upgraded (say) from 9.10 to 10.04?

---

### Post by Calash on 2010-04-27
> **Paddy Landau said:**
> Yes. Modern encryption methods, *when done properly*, are so secure that in practical terms they are unbreakable. If it contains military state secrets or details of a child pornography ring, a government might spend the money and time to break it, but for the average user, it's not going to be broken.

That was not my point.  I was responding to your analogy of a safe and having the passphrase being like the combination.  It is actually a good analogy to show my point.  With the combination you can easily open the front door and access your goods at any time.  This is how encryption works as well.  As long as you have the token/password you can get in the front door, being the installed OS.

What happens when the front door breaks on our theoretical safe? (Lets imagine the safe is made by Microsoft for a moment :) ).  It is the same as if your Operating System no longer boots.  Your combination no longer works and the easy access is gone.  Sure you can get in but it takes a ton of work to do so.  You have to drill the lock out, or cut of hinges.  Ether way it is a lot of work to get in.

This same principal applies to encryption, for better or worse.

> 
If you have your passphrase, why prevent you from accessing your data just because you booted from a Live CD and not from the installed OS?



Because encryption is not defending against somebody sitting at your computer typing on a keyboard.  It is defending somebody who snagged your laptop from a coffeehouse, or somebody who lifted a drive image and wants to get your corporate secrets.  If all that stands between them and your data is a single passphrase then it is just a matter of time before they get the data.  

On a side note, I think the method of encryption done by Ubuntu is a waste of time for everybody but corporate clients with Laptops.  Based on my experience Desktops are never the target of such a theft, as a Laptop can easily be dropped in a bag and never seen again.  Somebody who has your drive but not your password, the first thing they will try is a liveCD type environment.

Personal opinion, so take that last part with a grain of salt :)

---

### Post by Paddy Landau on 2010-04-27
> **Calash said:**
> That was not my point...
Yeah, OK, but for your average user, nevertheless we want it easy to get in if you have the key, hard to get in if you don't. That's all.

Otherwise you get the situation where the user (or service technician) reinstalls the OS because it failed or it's being upgraded, and the poor user can't get his own data. (I've seen some threads on the forum where that has happened.) That's going to give Ubuntu a bad name!

I think it's a matter of personal opinion here. You see it as, "OS = safe, key = door of safe;" whereas I see it as, "encryption = safe, key = door of safe, OS = any pair of hands." So we can argue until the cows come home and never agree. We'll have to beg to differ on this one.

---

### Post by ddrake_ on 2011-05-31
Perhaps this link will be useful to the OP: [http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html). It seems to apply to exactly this situation: boot from CD, recover ecryptfs-encrypted stuff.

---

