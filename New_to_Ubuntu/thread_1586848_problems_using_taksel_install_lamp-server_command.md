---
title: "problems using taksel install lamp-server command"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by thorbs on 2010-10-02
I am trying to install lampp on my computer with the taksel install lamp-server command but get following:


sudo tasksel install lamp-server
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "dk_DK.UTF-8",
	LANG = "en_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "dk_DK.UTF-8",
	LANG = "en_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "dk_DK.UTF-8",
	LANG = "en_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TIME = "dk_DK.UTF-8",
	LANG = "en_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory
thorbjrn@thorbjrn-laptop:~$ ^C
thorbjrn@thorbjrn-laptop:~$

---

### Post by Hippytaff on 2010-10-02
have a peek of this

[http://ubuntuforums.org/showthread.php?t=138022](http://ubuntuforums.org/showthread.php?t=138022)

---

### Post by thorbs on 2010-10-02
thanks for the reply....

I have to admit though that it goes over my head, is it really completely beginner?

---

### Post by Hippytaff on 2010-10-02
Well.. this guy reakons typing this into the terminal (Command line thing - CTRL+ALT+T will open it) sorted a similar problem for him
```

sudo locale-gen

```
```

sudo dpkg-reconfigure locales
```

Though I'm new too so I'm don't know enough to gurantee it'll work :-s :-)

---

### Post by thorbs on 2010-10-02
ahhh ok, allready did that, did not work. But thanks.....

---

### Post by Hippytaff on 2010-10-02
just a punt but

```

sudo dpkg-reconfigure locales

```

---

### Post by thorbs on 2010-10-03
I found this fix:

The fix (change to whatever language or version of english you’re using eg en_GB):

apt-get install language-pack-en-base


export LANGUAGE=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_ALL=en_US.UTF-8
locale-gen en_US.UTF-8
dpkg-reconfigure locales



but I am not sure how it looks for danish. So if anybody let me know.


is it language-pack-dk-base?

---

### Post by thorbs on 2010-10-03
ok, that did not work either got the following message


perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "dk_DK.UTF-8",
	LC_ALL = "dk_DK.UTF-8",
	LC_TIME = "dk_DK.UTF-8",
	LANG = "dk_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/bin/bash: warning: setlocale: LC_ALL: cannot change locale (dk_DK.UTF-8)



bit lost here

---

### Post by Hippytaff on 2010-10-03
Might be wroth reading this - [https://help.ubuntu.com/community/Locale](https://help.ubuntu.com/community/Locale)

---

### Post by thorbs on 2010-10-03
thanks, not much new information in that, anybody who knows a solution for this?

---

### Post by thorbs on 2010-10-06
Ok if no one can help, I will have to wipe the comp and start over. It would however be reasuring if I atleast could have known what went wrong....

---

### Post by kartikjagdale on 2010-10-25
I had the same problem 
but it got fixed

try the following command

dpkg-reconfigure locales


I hope this will solve your problem

---

