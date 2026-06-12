---
title: "Can ISO spread across more than one disk?"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by Kellemora on 2010-03-04
Hi Gang

I'm trying to learn something new before the new LTS comes out.
Currently running Hardy 8.04.

It was suggested I take my existing install and turn it into an ISO.

Since my /home is on a separate partition AND does not hold many data files, I store data on an external drive used sorta like a file server, and backed up off-site, so THAT does not need copied.

I was thinking the ISO would be a duplicate of what I have now, so I could reinstall just as I left it.  Including the /home directory and it's contents.

I'm not new, been using Ubuntu now, but not very well under the hood, need to examine my cheat sheets each time I need to do something involving admin or root.

Ubuntu just WORKS with no problems, so I rarely have to look under the hood!

Am I barking up the wrong tree thinking ISO?????
Even though that seems to be the recommended method.
And what if it covers more than one CD?????

Thank You

TTUL
Gary

---

### Post by undecim on 2010-03-04
I don't understand what you are trying to do. Are you trying to make a complete backup of your system to a CD?

---

### Post by sandyd on 2010-03-04
> **Kellemora said:**
> Hi Gang

I'm trying to learn something new before the new LTS comes out.
Currently running Hardy 8.04.

It was suggested I take my existing install and turn it into an ISO.

Since my /home is on a separate partition AND does not hold many data files, I store data on an external drive used sorta like a file server, and backed up off-site, so THAT does not need copied.

I was thinking the ISO would be a duplicate of what I have now, so I could reinstall just as I left it.  Including the /home directory and it's contents.

I'm not new, been using Ubuntu now, but not very well under the hood, need to examine my cheat sheets each time I need to do something involving admin or root.

Ubuntu just WORKS with no problems, so I rarely have to look under the hood!

Am I barking up the wrong tree thinking ISO?????
Even though that seems to be the recommended method.
And what if it covers more than one CD?????

Thank You

TTUL
Gary
a) im sure it will go over 1 cd.
b) not sure about if it will work when you already have files, but you can use raid 0 to make one large drive out of multiple drives (make sure you use raid 0). If you dont have hardware raid or fakeraid, you can use software raid (mdadm)
c) not a good idea to back up to an ISO. You cant just reinstall the iso just like your reinstalling ubuntu.

---

### Post by lisati on 2010-03-04
[remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") can help make a Live CD of your installation, but you will have to take care of your data files separately.

---

### Post by Kellemora on 2010-03-05
Thanks guys

I must be thinking along the wrong lines, as usual.

Seems I've read very many times to make an ISO of your system, before you do an upgrade.  That way you can go back to where you were?

In my near 40 years of using computers, I've NEVER had a backup/restore function properly, so I don't even consider that route anymore.

I usually just reinstall the OS, and each and every program I had installed one by one, which can take quite a long time.

And as I said, all user DATA files are stored outside of the computer, but user settings for each program are still in the computers, and that's why I was thinking of making some type of restore disk.

I'll reread some of the comments that made me think using an ISO was the way to go?????  I probably misread them, hi hi.........

TTUL
Gary

---

### Post by swoll1980 on 2010-03-05
Use clonezilla, and make a hard disk image put it on a little portable hard drive or flash drive. This is nice for when you make boo boos

---

### Post by Kellemora on 2010-03-05
I think I'm going to take the CHICKEN way out and pull the hard drive and install a new hard drive to try out the new LTS when it comes out.

That way if I have problems, I can pop the old drive back in again!

I'm even Leery of using separate partitions, even though most of my machines are currently dual or triple boot as it is.

I have /home on it's own partition and like it that way, BUT I have to have a /home partition for each distro, which if recall from 2 years ago when I set up triple boot, it was a nightmare to keep a separate /home for each distro......  I apparently figured it out since all of my machines work just fine, but I have very bad memory on how I did things.

TTUL
Gary

---

