---
title: "can't write a password for being root in a terminal"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Flywaver on 2009-03-02
Hi,

I am having a hard time getting root...if I do su it then asks for the root password but when I type the password nothing happens...tue black cursor deoesn't move! :(

Also, i login automatically with my username so I can't even select root when it boots up!

Any help would be greatly appreciated!

Cheers!

---

### Post by muteXe on 2009-03-02
You are typing something, it just doesn't show anything.  It's a security precaution so no one looking over your shoulder can see it.
Just press enter after you've entered your password in.  It should still work.

---

### Post by Dougie187 on 2009-03-02
Also, root is locked out, so you shouldn't be able to log in as root. This is another security measure, as if you could log in as root someone could (in theory) brute force their way into your computer as root and take it over. And you wouldn't be able to do a thing.

There are ways to enable root, but I believe they are not allowed to be given out in the forums. Also, it is highly not recommend to do that. If you need root, just use sudo, or su. but sudo should be sufficient for most things.

---

### Post by overdrank on 2009-03-02
> **Flywaver said:**
> Hi,

I am having a hard time getting root...if I do su it then asks for the root password but when I type the password nothing happens...tue black cursor deoesn't move! :(

Also, i login automatically with my username so I can't even select root when it boots up!

Any help would be greatly appreciated!

Cheers!

Hi and this link will help [RootSudo]("https://help.ubuntu.com/community/RootSudo")
 [Forums policy ]("http://ubuntuforums.org/showthread.php?t=716201")on root login

---

### Post by taurus on 2009-03-02
If you need to have root privilege, use sudo (not su by itself since that requires you to have root password).  

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Flywaver on 2009-03-02
Thanks all...I used: gksudo :)

---

### Post by Tek-E on 2009-03-02
> **Dougie187 said:**
> Also, root is locked out, so you shouldn't be able to log in as root. This is another security measure, as if you could log in as root someone could (in theory) brute force their way into your computer as root and take it over. And you wouldn't be able to do a thing.

There are ways to enable root, but I believe they are not allowed to be given out in the forums. Also, it is highly not recommend to do that. If you need root, just use sudo, or su. but sudo should be sufficient for most things.


Are you serious?? you arent allowed to give the information out for how people can enable the root account on their systems on the forums???  I agree that they shouldnt be logging in as root but I also disagree.  They should be able to do whatever they want with their computer regardless of how insecure their system may become. as long as they realize the possible consequences of their actions.

---

### Post by prolapse on 2009-03-02
You can also use 'sudo su' or 'sudo -i' to get to a root prompt without having to unlock the root account completely.

---

### Post by llamabr on 2009-03-02
```
They should be able to do whatever they want with their computer regardless of how insecure their system may become. as long as they realize the possible consequences of their actions.
```

No one here forbids anyone to do anything with their system.  But it seems that we're all bound by the codes of conduct prescribed by the owner of the forum.  I suspect you agreed to TOS's when you logged in the first time, even if you didn't read them.

Ubuntu is designed for baby steps, where everything works and no one needs to know how if they don't want.   Probably other distros are more appropriate for those falling in the latter category.

---

### Post by Old *ix Geek on 2009-03-02
> **Tek-E said:**
> Are you serious?? you arent allowed to give the information out for how people can enable the root account on their systems on the forums???  I agree that they shouldnt be logging in as root but I also disagree.  They should be able to do whatever they want with their computer regardless of how insecure their system may become. as long as they realize the possible consequences of their actions.I totally agree.  I find this, and other forum policies, to be VERY insulting to the intelligence of forum members.  I've said before that just because someone is a beginner with Linux doesn't mean they're a clueless idiot, unable to understand instructions and/or concepts.  I mean, *I* did it.  It's been 24 years for me, but I "grew up," so to speak, at a command prompt, with full root privileges, and have NEVER had a problem because of it.  I use "su -" all the time, and, yes, I've enabled root logins at bootup, too.

---

### Post by llamabr on 2009-03-02
```
I totally agree. I find this, and other forum policies, to be VERY insulting to the intelligence of forum members.
```
I can't say I disagree.  There are a few policies like this.  We're also discouraged from suggesting the reading of the man page -- I've been officially "warned" against doing so, even without using the F word.

To be fair, I guess, the point of the policies, along with ubuntu, is to try to avoid scaring off new users with advice that sounds too scary on their first day.  They're absolute beginners, after all.

---

### Post by maybeway36 on 2009-03-02
I would just use
```
sudo -i
```
instead of su. It asks for your user password.

---

### Post by chrisod on 2009-03-02
> Are you serious?? you arent allowed to give the information out for how people can enable the root account on their systems on the forums??? I agree that they shouldnt be logging in as root but I also disagree. They should be able to do whatever they want with their computer regardless of how insecure their system may become. as long as they realize the possible consequences of their actions.

The reality is most of the people asking that question really don't need to be mucking about in a root account because they don't understand the consequences and won't bother to learn them. It has nothing to do with paternalism and everything to do with respecting the design decisions made in Ubuntu. If you want to enable root Google will teach you how in one click. In these forums we are expected to respect the developers decision to not have root enabled.

If it were up to me I add "How do I install whatever in wine" to the list of forbidden answers ;)

Kidding about wine...sort of.

---

### Post by presence1960 on 2009-03-02
I think it is a good policy to not tell everyone how to enable a root log in on the forums. I haven't been using Linux that long and figured out how to enable it in Ubuntu and Kubuntu. Guess what? After I enabled it and logged in once I changed it back for there really isn't a need for me to log in as root. You hear all the time to be careful with commands using sudo- just imagine the warnings with someone logged in as root for their entire session.

As for wine- I ignore all those because I am not particularly fond of wine. I will dual boot or use virtualization to run windows, this way EVERYTHING I want to run will definitely work.

---

