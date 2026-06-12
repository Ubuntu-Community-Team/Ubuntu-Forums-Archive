---
title: "encrypt"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by cartisdm on 2008-12-08
Is there an easy (read: GUI) way to password protect a folder in ubuntu?  I'm the only user on the computer so there's no point in restricting my user to the folder.

I noticed if you right click there's an option to "Encrypt" but that doesn't seem to be what I was looking for.

---

### Post by gettinoriginal on 2008-12-08
Your post is rather confusing.  If you are the only user, why do you need to protect one folder ?? (you don't have to answer that LOL)  Possibly transfer ownership of the folder to root ??  Just don't quite understand what you are trying to do.

---

### Post by binbash on 2008-12-08
truecrypt.org download for ubuntu and install

---

### Post by cartisdm on 2008-12-08
> **gettinoriginal said:**
> If you are the only user, why do you need to protect one folder ?? Possibly transfer ownership of the folder to root ??  Just don't quite understand what you are trying to do.

Yes, I am the only defined user but that doesn't keep friends, family, roommates, from saying "Oh hey, can I check my [insert email, facebook, uploaded pictures] on your laptop?"

I'm looking for a simple password protected way to protect my data.  It doesn't need to be super encrypted as I know there are a hundred ways around passwords (liveCDs etc.), but to the common user I'd like to feel safe with some of my folders.

---

### Post by Menschenfresser on 2008-12-09
If you are using Intrepid, you could use a guest session for your friends. They won't be able to access any other folders in the system and after they log out, the files they created are deleted. You could also combine this with a [private directory]("https://wiki.ubuntu.com/EncryptedPrivateDirectory"), examples [here]("http://dustinkirkland.wordpress.com/2008/10/03/whats-in-my-encrypted-private-directory/") (yes, I know it's not exactly what you asked)

---

### Post by jakupl on 2008-12-09
> **binbash said:**
> truecrypt.org download for Ubuntu and install

1+

I use truecrypt myself for all my sensitive stuff. It is very good and very simple. Has a nice GUI and impossible for even the us government to crack, if you use a strong password. Check it out.
However, you cannot encrypt a folder with it. It basically creates a file that will work as a folder. When it's locked, Ubuntu has no idea what it is. But when you open it through truecrypt, it will be mounted as a virtual hard disc and it will appear on your desktop. Everything you put into the virtual hard disc will be completely scrambled when you unmount it.

Sounds much more complicated than it is. Truecrypt is very intuitive.

---

### Post by hyper_ch on 2008-12-09
nothing is impossible to crack.

---

### Post by jakupl on 2008-12-09
> **hyper_ch said:**
> nothing is impossible to crack.

Yes. The current combined "computerpower" of the world can only do that much calculations. If the encryption is good and the password strong then it will take longer than the age of the universe to crack it, using the current technologies.

EDIT: though one weak point would be that Ext3 is a journaling file system. No way of knowing what a forensic would find, if it came to that.

---

### Post by hyper_ch on 2008-12-09
yet consider the increase in computer power over the last 5, 10, 20, 50 years ;)

---

### Post by gandaran on 2008-12-09
> I use truecrypt myself for all my sensitive stuff. It is very good and very simple. Has a nice GUI and impossible for even the us government to crack, if you use a strong password.
you really do believe this don't you? CIA can crack any encrypted file in seconds!
most encrypt software have a backdoor (reason why some encrypting sofware is illegal in USA), this backdoor is only supplied to security agencies and if the application doesn't have this backdoor CIA and the likes have ready made cracking tables (like rainbow tables), nothing is secure!

---

### Post by hyper_ch on 2008-12-09
> **gandaran said:**
> CIA can crack any encrypted file in seconds!
Reference?

> **gandaran said:**
> most encrypt software have a backdoor
Reference?

> **gandaran said:**
> CIA and the likes have ready made cracking tables (like rainbow tables), nothing is secure!
And in what cases do rainbow tables provide a faster alternative to get a password?

---

### Post by gandaran on 2008-12-09
> **hyper_ch said:**
> Reference?


Reference?


And in what cases do rainbow tables provide a faster alternative to get a password?
reference, well I can't give you any, this is supposed to be state secrets!
but I can tell you I'm very curious and have googled for every bit of  information about encrypting software and tried all sorts of cracking software in windows and linux, conclusion? nothing is safe!

---

### Post by Pjotrovitz on 2008-12-09
OK, state secrets aside, if you open the run dialogue(alt+f2) and type gksudo nautilus, you can then navigate to the folder you want protected and open it's properties. Here choose root as the owner with all permissions, everyone else should have no permissions. After that, only root (aka gksudo nautilus or sudo commands) can access the folder.

---

### Post by iKonaK on 2008-12-09
I use, on hardy, truecrypt for small files and encfs for a larger amount of data; as it's already been said, to get truecrypt go to their webpage and for encfs > "sudo apt-get install cryptkeeper".
As for the degree of security, encryption can provide, i must say that no encryption is bullet proof; but the point of encryption, as far as i know, is to create decrypting whithout the proper pass/key a big pain in the a*ss :)

---

### Post by scorp123 on 2008-12-09
> **gandaran said:**
> CIA can crack any encrypted file in seconds! I seriously doubt that :lolflag:

> **gandaran said:**
>  most encrypt software have a backdoor If they are from Microsoft, yes maybe. But that's the beauty about open source software: no backdoors. If there were backdoors people would spot them and remove them.

> **gandaran said:**
>  (reason why some encrypting sofware is illegal in USA) And you sure got that wrong. Such stuff is not illegal in the USA (free speech), but it's illegal to **_export_** certain crypto software from the USA to countries such as Iraq, Iran, Cuba, and so on. And why? Because the US government fears that it would be impossible for them to eavesdrop on their enemies if they are no longer able to crack Cuban, Iranian, <insert enemy here> messages. It's a silly policy anyway, because those countries can easily obtain strong cryptographical know-how by many other ways and not just via US software.

> **gandaran said:**
>  nothing is secure! While that may be true, your story above sure has some of its facts wrong and is slightly exaggerated ;)

---

### Post by gandaran on 2008-12-09
> **Pjotrovitz said:**
> OK, state secrets aside, if you open the run dialogue(alt+f2) and type gksudo nautilus, you can then navigate to the folder you want protected and open it's properties. Here choose root as the owner with all permissions, everyone else should have no permissions. After that, only root (aka gksudo nautilus or sudo commands) can access the folder.
thanks for this information, I hadn't thought about this, but it is good indeed, no need for encrypting, its good enough for hiding information fron prying eyes! 
by the way I do have a lot of encrypted files on my computer but I just use encrypted zip or rar files for my needs.

---

### Post by hyper_ch on 2008-12-09
> **gandaran said:**
> reference, well I can't give you any, this is supposed to be state secrets!
but I can tell you I'm very curious and have googled for every bit of  information about encrypting software and tried all sorts of cracking software in windows and linux, conclusion? nothing is safe!
Well, for truecrypt, luks/dm-crypt you can look at the source. Please point out the backdoor to me in those two....


> **Pjotrovitz said:**
> OK, state secrets aside, if you open the run dialogue(alt+f2) and type gksudo nautilus, you can then navigate to the folder you want protected and open it's properties. Here choose root as the owner with all permissions, everyone else should have no permissions. After that, only root (aka gksudo nautilus or sudo commands) can access the folder.
Everyone but he who boots from a live cd or takes the harddisk out and puts it into another computer...
Depending on whome you're afraid of this might be enough...

---

### Post by Pjotrovitz on 2008-12-09
> **hyper_ch said:**
> 
Everyone but he who boots from a live cd or takes the harddisk out and puts it into another computer...
Depending on whome you're afraid of this might be enough...

Well, he wanted to keep his files from prying family borrowing his comp to check their mail.. I guess we ain't talking about international spy agencies here..

---

### Post by gandaran on 2008-12-09
> And you sure got that wrong. Such stuff is not illegal in the USA (free speech), but it's illegal to export certain crypto software from the USA to countries such as Iraq, Iran, Cuba, and so on. And why? Because the US government fears that it would be impossible for them to eavesdrop on their enemies if they are no longer able to crack Cuban, Iranian, <insert enemy here> messages. It's a silly policy anyway, because those countries can easily obtain strong cryptographical know-how by many other ways and not just via US software.
One that isn’t legal in the USA. All encryption software made in the USA must provide a crack to law enforcement.[http://www.seasonsecurity.com/what-is-the-best-and-most-secure-file-encryption-software-64275](http://www.seasonsecurity.com/what-is-the-best-and-most-secure-file-encryption-software-64275)

---

### Post by DGortze380 on 2008-12-09
Discussion is on it's way out... but...

Nothing is 100% secure. Given enough time and cycles, any encryption can be broke. Period.

The point is the make the level of security higher than the value of the data. 

If some wants your credit card number off an encrypted drive, they will get it, eventually. 

If they just want a credit card number that they can exploit... they're not going to spend 100 hours to get it, they probably won't spend 2 hours to get it... because they can pick 10 phone numbers out of the phone book and phish maybe 2-4 card numbers if not more in that 2 hours.

---

### Post by scorp123 on 2008-12-09
> **gandaran said:**
> One that isn’t legal in the USA. All encryption software made in the USA must provide a crack to law enforcement. Reposting something that was posted anonymously before on another forum doesn't make it true. ;)

Besides: depending on the type of software and depending on the algorithm used "providing a backdoor key to law enforcement" might even be impossible. That's why you should only trust open source software and "proven to work" algorithms that have been scrutinized by crypto experts.

---

