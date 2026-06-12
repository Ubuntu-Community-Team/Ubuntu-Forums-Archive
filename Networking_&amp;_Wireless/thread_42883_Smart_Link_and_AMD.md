---
title: "Smart Link and AMD"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by pace_tua on 2005-06-19
[resolved]
Used Stupid Mode with wvdial
[/resolved]

Hello. Linux newbie here.

I have Ubuntu dual booted on my laptop (AMD64m 3400), and have had only a few complaints that look to be fixable. However, for my modem, Smart Link 56k, I am unable to use the packages ([http://ubuntuforums.org/showpost.php?p=117356&postcount=34)]("http://ubuntuforums.org/showpost.php?p=117356&postcount=34%29").

Is there any way to possibly get my modem to work some other way?

Thank you for your help.

---

### Post by FLeiXiuS on 2005-06-19
[http://ubuntuguide.org/#installsmartlinkdriver](http://ubuntuguide.org/#installsmartlinkdriver)

Take a look here :-)

---

### Post by pace_tua on 2005-06-19
I cannot use this package either because the architecture is different :-?

---

### Post by FLeiXiuS on 2005-06-19
What arch are you using?

---

### Post by pace_tua on 2005-06-19
[QUOTE=FLeiXiuS]What arch are you using?[/QUOTE]
 AMD64

---

### Post by FLeiXiuS on 2005-06-20
So I take it your on 64bit Hoary also then?

In this case you could see if the packages are available in the multiverse.  I believe they are!

$ sudo apt-get install sl-modem-source
$ sudo apt-get install sl-modem-daemon

From them you can cd /usr/src and extra the source.  Then compile the source for your kernel and you should be good to go.

---

### Post by pace_tua on 2005-06-20
[QUOTE=FLeiXiuS]So I take it your on 64bit Hoary also then?

In this case you could see if the packages are available in the multiverse.  I believe they are!

$ sudo apt-get install sl-modem-source
$ sudo apt-get install sl-modem-daemon

From them you can cd /usr/src and extra the source.  Then compile the source for your kernel and you should be good to go.[/QUOTE]
 Okay, will do.

Thanks, I'll be back with the report.

---

### Post by pace_tua on 2005-06-20
I've run into another problem:roll:

When I run the command [color=Sienna]sudo apt-get install sl-modem-modules[/color], I recieve an error telling me that sl-modem-modules cannot be found. So I did a little reading in the man pages and discovered the sources.list file.

Am I supposed to add my CD or directory to this? When I tried, I recieved errors stating that my "input" was incorrect for the following entry: [color=Sienna]deb file:/home/billy/ubuntupkgs[/color]. For adding a CDROM, I get the error that the CD is not a debian cd when using the [color=Sienna]apt-cdrom add[/color] command.

Quite confused...

---

### Post by pace_tua on 2005-06-21
I've definitely have been learning my way around linux lately... :-\"

Forgoing the [color=Sienna]apt-get[/color] command, I went back to [color=Sienna]dpkg[/color] and forced the install. So now I have the packages compiled, but I am still unable to detect my SmartLink Modem.

I think I'll head over to the AMD dedicated forum and post my problem.

---

### Post by pace_tua on 2005-06-21
I installed the x86 Hoary, dpkg the packages, rebooted, and was able to detect my modem.

But I cannot dial ](*,)

When I activate my modem in Settings->Admin->Networking nothing happens, it just says Activated, but deactivates once I close the window.

By adding the Modem option to my panel and activating it from there, I get a step farther. A dialog windows comes up asking if I want to connect. The first time I click OK, there is a split second where another window comes up with what looks like a progress bar, but it is so fast that I cannot see much. This only happens the first time while in a session. And there is no activation.

Help?

(sorry for the triple posting)

---

