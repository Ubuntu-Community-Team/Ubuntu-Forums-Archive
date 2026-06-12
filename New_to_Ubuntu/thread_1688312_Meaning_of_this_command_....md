---
title: "Meaning of this command ..."
date: 2011-02-15
forum: New to Ubuntu
---

### Post by opensource10 on 2011-02-15
Hello Expert...

I have a question here, I want to install application via terminal. The command to execute the file as below...
```

popcorn:/usr/local/fw1-loggrabber# ls
bin  etc  man  share
popcorn:/usr/local/fw1-loggrabber# cd etc
popcorn:/usr/local/fw1-loggrabber/etc# ls
fw1-loggrabber.conf  lea.conf
...
popcorn:/usr/local/fw1-loggrabber# cd bin/
popcorn:/usr/local/fw1-loggrabber/bin# l
total 6376
-rwxr-xr-x 1 root root 2406948 2005-02-21 14:42 fw1-loggrabber
-rwxr-xr-x 1 root root 2109388 2011-02-15 12:02 opsec_pull_cert
-rwxr-xr-x 1 root root 1997504 2011-02-15 12:02 opsec_putkey

popcorn:/usr/local/fw1-loggrabber/bin#./fw1-loggrabber [COLOR=DarkOrange]**-c**[/COLOR] /usr/local/fw1-loggrabber/etc/fw1-loggrabber.conf [COLOR=DarkOrange]**-l**[/COLOR] /usr/local/fw1-loggrabber/etc/lea.conf
```I am just wondering what is the meaning '[COLOR=DarkOrange]**-c**[/COLOR]' and '**[COLOR=DarkOrange]-l[/COLOR]**' over there?

Thank you for sharing ;)

---

### Post by AlphaLexman on 2011-02-15
> **opensource10 said:**
> I am just wondering what is the meaning '[COLOR=DarkOrange]**-c**[/COLOR]' and '**[COLOR=DarkOrange]-l[/COLOR]**' over there?
I don't know exactly, but most executable binaries will accept the **-h** or **--help** options.
```
/usr/local/fw1-loggrabber/bin/fw1-loggrabber --help
```

---

### Post by opensource10 on 2011-02-16
> **AlphaLexman said:**
> I don't know exactly, but most executable binaries will accept the **-h** or **--help** options.
```
/usr/local/fw1-loggrabber/bin/fw1-loggrabber --help
```

Hi AlphaLexman,

Thank you for your respond. I have tried your suggestion..and that's right, I could see the information ... \\:D/
```


popcorn:/usr/local/fw1-loggrabber/bin# ./fw1-loggrabber --help

Usage:
 ./fw1-loggrabber [ options ]
  -c|--configfile <file>     : Name of Configfile (default: fw1-loggrabber.conf)
  -l|--leaconfigfile <file>  : Name of Leaconfigfile (default: lea.conf)

-- output is omitted --


```

---

