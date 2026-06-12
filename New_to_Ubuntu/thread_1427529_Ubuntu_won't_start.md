---
title: "Ubuntu won't start"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by asharpham on 2010-03-11
I get the normal Ubuntu/Windows options to start (MBR) but if I select Ubuntu, I get a black screen with a login option. I enter my username and password and then a terminal style prompt comes up: alan@alan-laptop:

What do I do from here?

Alan.

---

### Post by spiky001 on 2010-03-11
is this a new install or have you been using ubuntu

---

### Post by jamesbarnhill on 2010-03-11
> **asharpham said:**
> I get the normal Ubuntu/Windows options to start (MBR) but if I select Ubuntu, I get a black screen with a login option. I enter my username and password and then a terminal style prompt comes up: alan@alan-laptop:

What do I do from here?

Alan.
It could be one of several things: 

1. Some system files were deleted (you could boot into a live CD and check around on your hard disk for missing files, but you would need to know what you're looking for.).  
2. Your RAM is flakey (if you have any other RAM modules you could try them, though if you can boot into any live cd this isn't the problem.).
3. Your HDD connection isn't good (check the lines going to your hard drive, make sure they are secure...this is what happened to me.)
4. X server for some reason or other hasn't started (try typing "startx" without the quotes, then hitting the enter button.)

Have you booted into it before, or is this after a new install?

---

### Post by era86 on 2010-03-11
Did you  make sure to install the Desktop version, and not the server?

If so, your X serv might be screwed.  After you login, type "startx" into the terminal.

Edit: See above post!

---

### Post by asharpham on 2010-03-11
Thanks guys. I'll try one or all of those suggestions. I have been using Ubuntu for several months so it's not a new install. And it's currently installed on a usb stick. I have Windows on my HD and I'm working towards being able to format the HD and installing Ubuntu there, using Virtualbox to run Windows for those (very few) programs that I can't run in Ubuntu.

I'll post here what happens.

Alan.

---

### Post by audiomick on 2010-03-11
You can check your RAM with the "memtest" option in the boot menu of the live CD. Let it run for a while. I think it needs a good hour or so for a single complete pass. It should show zero errors.

---

### Post by asharpham on 2010-03-11
I get 2 Memtest options in the bootup menu. Which should I try?

I started up again and entered "startx" and got this error message: There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256).

I hope this makes sense to someone. Any ideas what I do from here?

Alan.

---

### Post by albert s on 2010-03-11
could the usb stick have become corrupted?
I have had some lose files etc, whilst other files on the same stick were fine.

---

### Post by jamesbarnhill on 2010-03-11
> **asharpham said:**
> I get 2 Memtest options in the bootup menu. Which should I try?

I started up again and entered "startx" and got this error message: There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256).

I hope this makes sense to someone. Any ideas what I do from here?

Alan.
Hello Alan, I Googled (haha, of course) your error code and found this: (type it into the terminal, ;)) sudo chown-Rc your_username_here /home/your_username_here

I haven't had this problem so I don't know if it will work...but, there you go.

---

### Post by asharpham on 2010-03-11
Well James, I tried that string and it just said about "chown" (without quotes) command not found. I'll google the error as well and see what else is available. Thanks for the clue.

Alan.

---

### Post by jamesbarnhill on 2010-03-11
> **asharpham said:**
> Well James, I tried that string and it just said about "chown" (without quotes) command not found. I'll google the error as well and see what else is available. Thanks for the clue.

Alan.
Sorry Alan, that was my mistake, it's sudo chown -Rc your_username_here /home/your_username_here  The -Rc is a modifier, I missed the space...Sorry about that.

---

### Post by asharpham on 2010-03-11
I googled the error and found another couple of things to try so will let you know how I go.

---

### Post by asharpham on 2010-03-11
To be honest, I think I did include the space. I've tried everything that's been suggested so far except the memtest but to no avail. Nothing changes. I still get the login request. Thank goodness I can still access Windows so I can continue using this forum.

If anyone has any other suggestions I'd be glad to try them but otherwise I think I'll hav e to bite the bullet and reinstall.

Alan.

---

### Post by jamesbarnhill on 2010-03-11
I don't know, but you might have to try "startx" again.
If you do reinstall, please backup your home folder..:)

---

### Post by bonethug on 2010-03-11
asharpham,

Try to reconfigure xserver with the following command and tell me, if the error is still present:

As normal user: ```
dpkg-reconfigure xserver-xorg
```As super user: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by asharpham on 2010-03-11
Thanks Bonethug. I logged in as superuser and got this message: could not open /usr/cache/debconf/config.dat

Alan.

---

### Post by bonethug on 2010-03-11
Is that everything you've pasted from the output or is there any permission denied message or something?

---

### Post by asharpham on 2010-03-12
Nothing about permissions but here's the full output.
After I type sudo su, I get:
*root@alan-laptop:/home/alan#*
Then i type the stuff you told me to and this comes up:
*debconf: DbDriver "config": could not open /usr/cache/debconf/config.dat*
and it goes back to the root@ prompt.

---

### Post by asharpham on 2010-03-18
Nothing I tried worked so I've reinstalled Ubuntu and lost whatever wasn't backed up. This means there is no need to post any more replies here but I won't mark this as solved because it isn't.

---

