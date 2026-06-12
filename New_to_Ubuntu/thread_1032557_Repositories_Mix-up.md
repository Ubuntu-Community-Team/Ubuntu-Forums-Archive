---
title: "Repositories Mix-up"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by smith_fan on 2009-01-06
I screwed-up my Software Sources and now receive an error whenever I run the Update Manager.  I've not been able to locate a list of the repositories that should be present on a “standard” 8.10 installation.

I have not learned enough, yet, to be able to perform the needed re-installation of Intrepid w/o losing everything. [SIZE="1"](I've got a real multi-booting **nightmare** going on here...) [/SIZE]:frown:

Can you please tell me which repositories should be listed in Software Sources “out-of-the-box”?

Thanks a lot!,
~D~

---

### Post by Elfy on 2009-01-06
You should be able to use this to recreate a sources list - you're wlecome to mine but it's a bit added to :)

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by LowSky on 2009-01-06
could you post a copy of your list so we know what you did wrong, just telling you might not fix anything
type this in a terminal and copy paste the results...thanks
```
gedit /etc/apt/sources.list
```

---

### Post by ibuclaw on 2009-01-06
This is essentially the default repositories (This is a computer that has had ubuntu dist-upgraded since Feisty, rather than a clean install)

**Hardy:**
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe

# Partner Repositories
deb http://archive.canonical.com/ubuntu/ hardy partner

```

**Intrepid:**
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe

# Partner Repositories
deb http://archive.canonical.com/ubuntu/ intrepid partner

```
Note, this is for the UK Servers, but you can change the Servers from the Software Sources app in:
**System -> Administration -> Software Sources**

Regards
Iain

---

### Post by smith_fan on 2009-01-06
Here is my sources.list:  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse #Added by software-properties
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) IntrepidstableUS/

I really appreciate all of your helpful input!!:P

Thanks!:D,
~D~

---

### Post by ibuclaw on 2009-01-06
> **smith_fan said:**
> Here is my sources.list:  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main universe restricted multiverse #Added by software-properties
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) IntrepidstableUS/

I really appreciate all of your helpful input!!:P

Thanks!:D,
~D~

The last line in your sources file:
```
deb http://http.us.debian.org/debian IntrepidstableUS/
```
Is an invalid source.

Remove it and save/quit.

Regards
Iain

---

### Post by smith_fan on 2009-01-06
My 'Third-Party Software' tab would then be blank, if I'm not mistaken. :o  It was nearly taking-up that whole window before I did my ignorant modifying which led to this problem! :confused:

Do I need to put anything back in there? 	Question

Also, can you tell me what's the best way to make a backup copy of the etc folder?

Thanks for your help!,
~D~

---

### Post by smith_fan on 2009-01-06
When I try to do as you suggested, I am not allowed.  Instead, I am greeted with an error message.
"
Could not save the file /etc/apt/sources.list.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
"
I provided the same credentials that allow me to act as superuser elsewhere.

Any thoughts?

Thanks!,
~D~

---

### Post by Elfy on 2009-01-07
```
gksudo gedit /etc/apt/sources.list
```

If you get an error - please provide the command you used, the up arrow in a terminal will go back through the history.

---

### Post by smith_fan on 2009-01-07
You are a wonderfully helpful individual, Pixie, and I thank you! :D

Unfortunately, in the terminal window where I pasted that command it didn't ever prompt for credentials or anything.  It's just sitting there with a blinking 'text-box' cursor. :(

I, obviously, haven't got a clue as to what it's not happy about now nor about how to change it to make it work for your intended purpose.

I will try to be more timely than I was this last time in responding.

Thanks!,
~D~

---

### Post by daydbai on 2009-01-08
> **forestpixie said:**
> 

if you get an error - please provide the command you used, the up arrow in a terminal will go back through the history.

+1

---

### Post by Elfy on 2009-01-08
> **smith_fan said:**
> You are a wonderfully helpful individual, Pixie, and I thank you! :D

Unfortunately, in the terminal window where I pasted that command it didn't ever prompt for credentials or anything.  It's just sitting there with a blinking 'text-box' cursor. :(

I, obviously, haven't got a clue as to what it's not happy about now nor about how to change it to make it work for your intended purpose.

I will try to be more timely than I was this last time in responding.

Thanks!,
~D~
That command should open the file in a text editor with root rights. If it's not working I would have to ask if you're using ubuntu.

---

### Post by smith_fan on 2009-01-08
I dunno what changed (other than the time), but attempting the same thing this morning did produce a different response.  After prompting for my password, this opened:
"
## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse restricted universe main
# CDROMs are managed through the apt-cdrom tool.
"

I'm still pretty bewildered, but feel somewhat less persecuted now.

Thanks!,
~D~

---

