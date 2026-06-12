---
title: "how to log in as root?"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-12
how you log in as root?

ive never logged in as root on my machine.. linux newbie here 8-)

---

### Post by tom66 on 2009-04-12
It is forum policy not to tell users how to do this, sorry. See: [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

However, if you want to run a program with elevated privileges, try *sudo <command name>*. Or for a prompt, try *sudo -i*. You'll be asked for your password, but it'll remember it for 15 minutes.

---

### Post by lisati on 2009-04-12
Using "sudo" in front of the command line that requires root privileges is one of the main preferred methods here in the forums.

---

### Post by Rocket2DMn on 2009-04-12
Just as a general reminder, please don't explain to user's how to enable root, Ubuntu uses sudo as it's security model, so we need to support that.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
Thank you.

---

### Post by Craige4107 on 2009-04-12
Are you kidding me???  This is a security issue, not to tell???  Google it and see how easily this information is available.  Wow!!!!

---

### Post by nandemonai on 2009-04-12
> **Craige4107 said:**
> Are you kidding me???  This is a security issue, not to tell???  Google it and see how easily this information is available.  Wow!!!!

This isn't google, it's the _Official_ Ubuntu Forums.

---

### Post by Rocket2DMn on 2009-04-12
> **Craige4107 said:**
> Are you kidding me???  This is a security issue, not to tell???  Google it and see how easily this information is available.  Wow!!!!

How to enable root is not a secret, and can be easily found elsewhere.  However, we are here to support Ubuntu's security model, which has root disabled by default.  It should be our goal to educate users to follow this security model using sudo.

We aren't here to tell people how to use their systems, so if you have root enabled and think that you truly understand the risks and possible consequences of logging in as root, then you are free to do so.  But, this is not the Ubuntu way of doing things, so we don't support explaining how to enable root here.  This is a discussion that has been covered many times, and is outlined in the link I provided in my previous post.

I hope that helps.

---

### Post by lavinog on 2009-04-12
```
sudo -s
```
This will let you open a shell as superuser

before you use that though, you should ask why you think you need to login as root.
What are you trying to do? Maybe we can give you a better way of doing it.

---

### Post by jfbooth on 2009-04-12
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by llamabr on 2009-04-13
> **Craige4107 said:**
> Are you kidding me???  This is a security issue, not to tell???  Google it and see how easily this information is available.  Wow!!!!

You read the terms of service when you signed in, right?  If you think this is a bad security model,, probably you're giving advice on the wrong forum.

---

### Post by bodhi.zazen on 2009-04-13
> **Craige4107 said:**
> Are you kidding me???  This is a security issue, not to tell???  Google it and see how easily this information is available.  Wow!!!!

And setting a root password can also break a system. Since you are so fond of searching, search these forums and you will find threads where I have had to fix this problem.

So despite what a google search may yield, please be mindful of forums policy.

[Forums Policy Root Login]("http://ubuntuforums.org/showpost.php?p=5769207&postcount=77")

---

