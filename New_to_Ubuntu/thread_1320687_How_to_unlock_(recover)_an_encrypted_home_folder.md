---
title: "How to unlock (recover) an encrypted home folder"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-11-09
I installed Karmic on a computer and chose the option to encrypt the home folder.

All works fine.

The installation gave me 32-character unlock code in case I should need to recover the folder manually.

I want to test this, in case I should ever need to recover it.

So, how do I use that 32-character unlock code? I haven't managed to find the relevant documentation.

---

### Post by AlexanderDGreat on 2009-11-12
Dude, be careful, consider this case, I've Ubuntu 9.04, I installed from an alternate CD, I chose to encrypt the home folder. Then I reformated my PC. Setup was: formatted / and it's a separate partition, didn't format /home partition, but also a separate partition, finally, /swap is a separate partition. After installing Karmic, with these partitions / /home /swap, I can't login to my /home partition, you know why? Because it's encrypted. 

It preserved its configurations because I didn't reformat my /home. I've looked around almost 1 whole day, and reading about this problem, the experts say there's no work around for this yet. Here's the thread: [http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/](http://www.linuxquestions.org/questions/ubuntu-63/fresh-install-with-encrypted-home-partition-765465/)

But if you know any better or anyone out there thinks I'm wrong, you can start posting and help me clear this confusion out. Can't recover my /home files because of this. I suggest you backup now, don't use encryption yet, just keep a Wild Pitbull-Terrier w/ rabies to guard physical access to your pc.

---

### Post by Paddy Landau on 2009-11-12
Thanks for the warning! It seems terribly complicated.

I'll keep the folder encrypted (in case of theft), but at the same time I'll keep full backups.

That should cover both bases.

But, then, going back to my first point, what is the point of the 32-character unlock code? It's supposed to be in case the password is lost; but then surely that would allow reinstallation?

---

### Post by molder on 2009-11-12
Now I am scared, I don't have the 32-character unlock code.  Do you know of anyway to recover it?

---

### Post by ukripper on 2009-11-12
> **molder said:**
> No I am scared I don't have the 32-character unlock code.  Do you know of anyway to recover it?

There is no way to unlock if you don't know the passphrase, otherwise it defies the whole purpose of encryption in first place!

---

### Post by Paddy Landau on 2009-11-12
> **molder said:**
> Now I am scared, I don't have the 32-character unlock code.  Do you know of anyway to recover it?
No. When I installed Karmic with the encrypted folder, it told me to make a note of it then. As far as I know, there's no recovery mechanism.

Make a full backup! (That *should* go without saying.)

> **ukripper said:**
> There is no way to unlock if you don't know the passphrase, otherwise it defies the whole purpose of encryption in first place!
The 32-character unlock code is there in case you forget your password. As I understand it (and I may be wrong), the system generates a key to encrypt and decrypt, and your password unlocks that key. The 32-character unlock code is that key.

Obviously, you would need to keep your unlock code physically separate from your computer, preferably in a different building!

---

### Post by anaconda on 2009-11-12
> **Paddy Landau said:**
> Thanks for the warning! It seems terribly complicated.

I'll keep the folder encrypted (in case of theft), but at the same time I'll keep full backups.

That should cover both bases.

But, then, going back to my first point, what is the point of the 32-character unlock code? It's supposed to be in case the password is lost; but then surely that would allow reinstallation?

I just cant understand why do so many people want to encrypt the whole home folder.

I have 1-2 2GB encrypted files, which can be mounted at any time I want to. eg. any time I need to access them. I keep all my "sensitive" data in them.

The advantages:
If I need borrow my laptop to a friend for a couple of hours, I can do that. What about you? the machine wont work, if you don't "unlock" it, and if you do, your friend will have access to all your sensitive data also..hmm..

No problems of not beeing able to boot the machine, if you forgot the password, and no need to enter any password when booting the machine for a quick internet serf..

etc..

---

### Post by Paddy Landau on 2009-11-12
> **anaconda said:**
> I just cant understand why do so many people want to encrypt the whole home folder.
Where do you keep your emails? All your documents? What about your conversations on Skype? Are they all encrypted?

For a normal home user, it's probably of no great consequence.

But for a professional who deals with many clients' sensitive and confidential issues through email, Skype and MSN, and who stores many details in various documents, it is of great consequence should the computer be stolen.

---

### Post by AlexanderDGreat on 2009-11-12
> **Paddy Landau said:**
> But, then, going back to my first point, what is the point of the 32-character unlock code? It's supposed to be in case the password is lost; but then surely that would allow reinstallation?

Yes, I agree! But what I can't understand. When I reformatted / of Ubuntu 9.04, but not the home folder, isn't the installation of Karmic suppose to ask me, 

"Hey, what's the password for that encrypted home folder you setup in Jaunty so you can use your home folder again in Karmic? I'm only doing this in case you stole this computer and reformatted the system to access the HOME FOLDER."

BUT HELL NO. It will leave you dead cold with a mouse floating on a blank screen after logging in to your machine. If you swith to another terminal, and ls your /home - it only has 2 files, README.txt Access-Your-Private-Files.Desktop, which both don't contain anything.

So in this blog: [http://bodhizazen.net/Tutorials/Ecryptfs/](http://bodhizazen.net/Tutorials/Ecryptfs/) -it's clearly stated: 

"...there are as of yet no automated tools on the installation CD (alternate or desktop) to automatically preserve and configure your Ecryptfs encrypted /home directories.

I advise you **back up your data, install, then restore your data.**"

Hope to help.

PS This blog: [http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html) said, you can use LIVECD to get access to your /home folder, but still, this doesn't work for some people, including me. Good Luck!

---

### Post by Paddy Landau on 2009-12-08
Well, I seem to have found, finally, the answer to the question. I haven't had a chance to test it yet, but it is nicely documented.

Thanks to Dustin Kirkland... Mosey over to Linux Magazine's [Ubuntu's Encrypted Home Directory]("http://www.linux-mag.com/cache/7568/1.html") and read through. There are three pages; the third page holds the treasure.

---

### Post by blazemore on 2009-12-08
If there was a way to unlock an encrypted folder without a passphrase, the whole point of encryption would be ruined, because then anybody could just do the same thing you did!

---

### Post by Paddy Landau on 2009-12-08
> **blazemore said:**
> If there was a way to unlock an encrypted folder without a passphrase, the whole point of encryption would be ruined, because then anybody could just do the same thing you did!
Whoa! It's not without a passphrase!

When you install Ubuntu 9.10 and ask for an encrypted folder, it creates a 32-character passphrase. It stores this passphrase encrypted by your own password.

However, the installer tells you what the passphrase is, and warns you to save it and keep it safe in case you have to access your data with a Live CD.

That's the passphrase that Dustin Kirkland means. (If you haven't kept it safe, then you can't access your home folder should your Karmic die.)

I may have a chance to test this tomorrow.

---

### Post by Paddy Landau on 2009-12-09
> **Paddy Landau said:**
> Linux Magazine's [Ubuntu's Encrypted Home Directory]("http://www.linux-mag.com/cache/7568/1.html")...
It doesn't work, sadly.

I've left a post on the page.

---

### Post by Ghost|BTFH on 2009-12-09
Just a few notes...

#1: If you back up your sensitive data and that backup is not secure, neither is your data.

#2: If you write down a passphrase or an unlock code, your system is as secure as that piece of paper is.

#3: The ONLY time you would want to secure your entire home directory is if you were afraid someone would steal your computer and have access to your whole system.

#4: IF #3 is the case AND you would foolishly want to "lend" a "friend" your highly secure and confidential system with delicate client information (which is about as stupid as breathing acid), THEN you would logically set up your secured account separately from the common login account, so if you needed to lend someone your laptop, you would be able to do so without any issue - your /home/self folder would be encrypted and secured while they would be using the /home/guest section.

Of course, your BEST security (While allowing this annoying friend to keep borrowing your laptop when he really needs to go buy his own and quit mooching off you) would be to have the entire drive encrypted and have a secondary drive that could be swapped so your "friend" could use the laptop without any issue at all and the client data remains tucked away in a secure location (such as a safe).

#5: Communications with clients should NEVER be logged and kept in a commonly located folder - if they must be logged, the files should be cut and pasted into a secure backup, such as an encrypted usb drive that is kept on your person at all times.

There's the illusion of being secure and then there's actually being secure.

It sounds like you're looking more for the illusion - otherwise you'd be talking to a systems security specialist who would teach you how to think like this.

Cheers,
Ghost

---

### Post by Paddy Landau on 2009-12-09
Thanks for the replies, Ghost.

I'm aware of all these things that you mention, and they are good points for newbies.

In my case, the encrypted drive is not to guard against state secrets, but against casual thieves who would be unlikely to spend much time trying to crack the key (or even know that there is such a thing as a key).

Having gone through this route for a friend, I think that a secured backup will be far easier to manage than recovering from a disk.

---

### Post by Ghost|BTFH on 2009-12-09
You're welcome for the post, glad you're aware of the security levels and I'm sure you'll put the information to good use.

Secure backup is definitely an option if the data isn't sensitive to exposure but critical for record keeping.

Cheers,
Ghost

---

### Post by Paddy Landau on 2009-12-10
Ta da! I found the answer.

Check it out:
[Recovering Files from eCryptfs Encrypted Home]("http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/")

This should be in the official documentation.

---

### Post by electricmaster on 2011-05-02
Actually, it's not too hard to get your passphrase again.

Go to terminal and type in 

```

sudo ecryptfs-unwrap-passphrase /home/.ecryptfs/**username**/.ecrpytfs/wrapped-passphrase

```
and then it will say "Passphrase:" and you type in your user password and it will give you back your passphrase. If you can't access your account, you can do it from another account or a live CD, but if you do it from a live CD, make sure to do it from it's original mount point at /media/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/.

---

