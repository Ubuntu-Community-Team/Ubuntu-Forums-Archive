---
title: "GNOME doesn't start?"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by skinnyj on 2010-11-07
So recently, I just upgraded from 10.04 to 10.10. It was working fine for a while, but then it wouldn't detect anything connected via USB. I tried to find a way to manual mount, but couldn't find one. So I wandered off onto different topics, and then made the idiotic mistake of installing an Nvidia graphics driver.

I then restarted to let changes take effect, but when it started back up again, it only gave me a terminal-based login screen. No GNOME or anything. I tried using both of the recovery mode copies and both non-recovery mode copies and in all of them, the GUI wouldn't be there. It would be the same terminal. After I would login using the terminal, all I had was a command line to work with.

Any suggestions on what I should do to fix this (besides reinstalling Ubuntu)?
I have some music and other things that I need to save, so I want to make sure that reinstalling is the *absolute last thing* I want to do.

---

### Post by preston collins on 2010-11-07
hey i am haveing a problem somthing similar check out [http://ubuntuforums.org/showthread.php?t=1615940](http://ubuntuforums.org/showthread.php?t=1615940)

---

### Post by Crusty Old Fart on 2010-11-07
Sounds like everything really went down the terlit after you installed the Nvidia driver.
Have you tried to remove it using apt-get purge?

You might be able to get Gnome to fire up after you log in to the terminal and then issue this command:
```

sudo service gdm start

```

After we get over this hump, then we can work on mounting your USB drives.

---

### Post by skinnyj on 2010-11-09
> **Crusty Old Fart said:**
> 
Have you tried to remove it using apt-get purge?


I used lots of different syntax but couldn't find the right combination. But I will try to see if I can get it off using that.

Also, is there a command to list the packages that are installed so I can find the name of the driver?

Edit:
I should also mention that my copy of Ubuntu is installed on an external hard drive that moves between a few computers. (I rarely use it anywhere else besides my laptop and my work computer terminal.) So the USB mounting problem may be temporary. But why it is able to read/write to the External hard drive and not be able to detect other USB connections is beyond me.

---

### Post by Crusty Old Fart on 2010-11-09
> **skinnyj said:**
> 
Also, is there a command to list the packages that are installed so I can find the name of the driver?

Yup...day sho' is:
```

dpkg --get-selections
***[COLOR=Red]If you use a grep filter for video, you might have an easier time finding it:[/COLOR]***[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]dpkg --get-selections | grep video

```These have also been helpful:
```

lsmod
[COLOR=Red]***...and...***[/COLOR]
lspci -tvv

```

---

### Post by skinnyj on 2010-11-09
Thanks.
I don't have my hard drive with me right now, but I will be able to try this tonight. I can probably come back with an update in maybe a day or two if I'm not swamped with work.

---

### Post by skinnyj on 2010-11-10
Update:
Problem solved. I couldn't exactly get my drive to boot up, but I was able to successfully retrieve my stuff and do a fresh install, so there shouldn't be any problems anymore. Thanks for all your help!

---

### Post by Crusty Old Fart on 2010-11-10
Good...glad to read that. Preston (post #2) ended up reinstalling as well. Haven't heard back since, so I reckon no news is good news.

Sometimes I think about how the hours and hours I've spent trying to fix a problem on my own system have been wasted when I could have just reinstalled and restored a backup of my /home directory in less than two hours. It's nuts.

Anyhow, I hope things work out well with the brand new shiny install.

Best of luck to you,

Crusty

---

