---
title: "Changed Mind About Unencrypted Home Directory"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Chrissd on 2011-02-24
Hi,

When installing Ubuntu, I was given the option of requiring a "password to login", or "encrypting and require a password to login".

I chose the first, and now I want to have an encrypted home directory. Is there any relatively easy way to encrypt the home directory and have it decrypted upon login?

Many thanks

---

### Post by An Sanct on 2011-02-24
How much time has passed after you installed? Because, encrypting after installation is a hassle, the simplest way is to reinstall, using the encryption option.

---

### Post by Chrissd on 2011-02-24
Will it be safe to copy my home directory contents and then just paste them into my new encrypted home, or would that cause problems with settings?

---

### Post by An Sanct on 2011-02-24
If you will copy whatever you have on desktop, it will be okay (and encrypted, when copied).

In the home directory there is also a lot of "*.name*", hidden folder, which contain settings, browsing cache, email client setup, ... etc. 

I would be careful about that (especially if you use compiz and know the hassle of setting it up)

At this point, I may not be the best one to give advice, since I didn't do anything like that yet, but according to [this thread]("http://ubuntuforums.org/showthread.php?p=9906323"), this should be [the solution]("http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/") (in short, yes. Copy *with hidden files*, should do it ...)

---

### Post by Chrissd on 2011-02-24
Nice one, many thanks!

---

### Post by Chrissd on 2011-02-28
I found an answer myself under this page:

[http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html](http://blog.dustinkirkland.com/2011/02/long-overdue-introduction-ecryptfs.html)

---

### Post by Kixtosh on 2011-02-28
Nice find Chrissd. That seems fairly simple, so I might try it myself later. It should be a lot easier than a whole install, with all user modified settings and preferences to change all over again, even if that's not that hard to do on anything five years old or less. (That's a rough guess, since anything with half decent specifications installs Ubuntu fast. PIII with less than 512 MB, for example, can take quite a while, so this procedure might be a lot simpler).

One word of note: if memory serves me correctly, and if you follow the instructions to encrypt swap as well, I suspect the suspend function may not work any more, so you might want to research that if you use it, and turn off automatic suspend settings, if you have any (mostly on laptops, to save battery when left inactive for too long), should by suspicion prove to be true.

---

### Post by Chrissd on 2011-02-28
Hi, actually, I have encrypted my swap now, and as a matter of testing I tried it. The computer will suspend and resume fine, but it now won't hibernate. Well, it hibernates fine, but it won't start up again.

---

### Post by Kixtosh on 2011-02-28
Great, thanks for the info! I'm going to go ahead and try this as well. I'll post back if I run into any problems so that others reading this can be aware of them.

I don't use hibernate anyway, since it takes much longer to activate than just shutting down (or suspend, obviously) on my laptops, and it takes almost as long to resume from hibernation on my laptops as a normal startup. Suspend is the only standby state that is really of any use to me normally, so it's good to know that this should work.

I mostly want to encrypt Home because I like to use the Chromium browser, and it doesn't encrypt stored passwords, apparently, making them vulnerable. Firefox does encrypt stored passwords, but I don't like the appearance of Firefox as much, because it uses up much more of the upper screen area than Chromium: an important consideration on smaller screen laptops such as those that I use (11" and 12").

---

### Post by KIAaze on 2011-02-28
> **Kixtosh said:**
> 
I mostly want to encrypt Home because I like to use the Chromium browser, and it doesn't encrypt stored passwords, apparently, making them vulnerable.

In that case, you could also just use an encrypted Private directory:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Then put ~/.chromium (or whereever chromium stores its passwords) into ~/Private and symlink to it.

That's what I use, because I'm afraid of loosing access to data in case I ever have hard drive problems or loose my encryption passphrase, while still wanting to prevent access to keys, passwords, etc stored in hidden config folders.

---

### Post by Kixtosh on 2011-02-28
Interesting, KIAaze, thanks! What would be the advantages of using an encrypted private directory instead of an encrypted Home folder, if you know of any?

---

### Post by KIAaze on 2011-03-01
Well, it's simple: Not everything gets encrypted, only what you put into the ~/Private folder.
If you encrypt your whole home folder, you'll have to create another folder outside /home/$USER to store things you don't want encrypted.

The thing is that if your hard drives gets a few errors (missing bits, etc), you might still be able to save most of your data if it's not encrypted.
If you loose the wrapped-passphrase file on your PC and any paper on which you've written it, your data is as good as lost.

---

