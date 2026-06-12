---
title: "Nautilus sorting case-sensitive"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by ofb on 2011-05-01
My Nautilus had just strated sorting case-sensitive.

A
C
b

instead of 

A
b
C

I'm using Ubuntu 10.04.2 LTS Lucid. My other Lucid box is still case-insensitive. How do I get rid of this case-sensitive setting?


Edit -- Just noticed my Opera bookmarks have been sorted case-sensitive too. Most annoying. Geequie and Dolphin have not been affected.

---

### Post by sisco311 on 2011-05-04
Please post the output of:
```
locale
```
and
```
locale -a
```

---

### Post by ofb on 2011-05-04
... I was just getting the output, and I see the machine is no longer case-sensitive.

I know I was still tripping over it yesterday morning, so perhaps something in yesterday's update pack changed it? I wish I understood. Here's the output for both boxes anyway.

```

n@grin:~$ locale
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=

n@grin:~$ locale -a
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

```

o@bluefish:~$ locale
LANG=en_CA.UTF-8
LANGUAGE=en_CA:en
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=

o@bluefish:~$ locale -a
C
en_AG
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```

Question: What causes case-sensitive sorting? I'm noticing online most people seem to be saying Nautilus is case-sensitive. Also a friend's Lucid install is case-sensitive. Why is mine different?

---

### Post by sisco311 on 2011-05-04
> **ofb said:**
> 
Question: What causes case-sensitive sorting? I'm noticing online most people seem to be saying Nautilus is case-sensitive. Also a friend's Lucid install is case-sensitive. Why is mine different?

The value of the LC_COLLATE environment variable determines how strings (file names...) are alphabetically sorted. The C or POSIX locale is case sensitive, others like  en_CA.UTF-8 or en_US.UTF-8 aren't. See: [uhelp]community/Locale[/uhelp]

Example:
```
env LC_COLLATE=POSIX nautilus --no-desktop
```
```
env LC_COLLATE=en_CA.UTF-8 nautilus --no-desktop
```

You can change your user's locale at the login screen or the system wide one with the update-locale command.

---

### Post by ofb on 2011-05-04
Thank you very much.

Mere details:

Just to confirm that I've got this right, the first command changes the line to "LC_COLLATE=POSIX" and the second to "LC_COLLATE=en_CA.UTF-8", right?

Er... where is that line, anyway? It's not in /etc/default/locale or /etc/environment.

And what does the argument "nautilus --no-desktop" do here? I'll guess only change Nautilus' sorting, which presumably wouldn't affect the Opera bookmark sorting.

---

