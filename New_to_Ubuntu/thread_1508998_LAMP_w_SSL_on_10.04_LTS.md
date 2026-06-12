---
title: "LAMP w/ SSL on 10.04 LTS"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by eldonjr79 on 2010-06-13
Hi guys, I’m totally new to Linux/Ubuntu and I just started my studies  on web development & programming. 

Thing is, the course I took taught  me the basics of HTML, CSS, Javascript, PHP & MySQL on Dreamweaver  and Zend (yes, running on MS Windows and WAMP). Thus, my questions:

1.  Does my distro (10.04 LTS AMD 64 Lucid Lynx) comes along with a LAMP  package (Apache, MySQL & PHP5) or the like*?  – I’m so newbie at Linux/Ubuntu I  just can’t check this out by myself… :S 

* if there’s an  alternative setup to LAMP preinstalled with my distro that’s fine with  me. I just need to know what it is and learn how to have my first steps on  it.

1.1. If so, how do I get started? I mean, how do I set up my stuff?  (PHPmyadmin, access localhost, etc).

2. What’s the best open source  alternative to Dreamweaver? What about Zend? Is it open source?

3. I just  got my own website hosted on a linux server and would also like to  manage it using SSL.Thanks, in advance!

Cheers,

---

### Post by Locke_99GS on 2010-06-13
If you installed (or will install) the server edition of Ubuntu, it will prompt you on what you would like installed and configured during the initial install on Ubuntu. During this time, selecting the LAMP stack components (and others, such as FTP, Mail, SMB/NFS, &c...) will install and configure them for you.

Otherwise, you can install the applications as you would install any other on Ubuntu/Debian, via an apt tool such as apt-get, aptitude, synaptic, software centre, &c... Most of the more commonly used server applications will run you through a setup process during installation.

---

### Post by eldonjr79 on 2010-06-13
Hey thanks Locke, the first option sounds interesting to me. Can I install ubuntu's server edition on a pc or even a laptop computer? If so, I guess I'd rather install it over my desktop version 'cause it seems fitter as I'll be practicing my web dev. skills and experimenting with personal website.

Thanks again,

---

### Post by sandyd on 2010-06-13
> **eldonjr79 said:**
> Hey thanks Locke, the first option sounds interesting to me. Can I install ubuntu's server edition on a pc or even a laptop computer? If so, I guess I'd rather install it over my desktop version 'cause it seems fitter as I'll be practicing my web dev. skills and experimenting with personal website.

Thanks again,

Ubuntu desktop = ubuntu server, except that it has different programs installed.

I guess that most books and stuff will tell you to use the default server config tool that is normally shown in ubuntu server when booting up.

however...
just go into the terminal and type in
```

sudo tasksel
```and select "LAMP"

there's your LAMP

oh, and btw, by default, files that the webserver serves are stored in /var/www

p.s.: a good tool to use for web developers and server (apache / mysql) is webmin ([http://webmin.com](http://webmin.com)).

it allows you to configure apache virtual hosts, which enables the hosting of multiple sites at once.

oh, and good luck, im a web developer myself :)

---

### Post by eldonjr79 on 2010-06-13
Hey Carlee, or should I say 'master' ? :) 

I have tried this 'magical' line you've shown to me on my terminal. It works fine until I select LAMP and hit enter. Then nothing happens, it just skips to the next prompt. Am I supposed to do so on a Ubuntu server distro instead? 

Thanks for your invaluable info and advice!

I'm just a newbie web developer who just finished an introductory course and is trying to put everything into practice now by creating and managing my own website -- I already have some friends requests but no way I can make and maintain professional websites now.

Bye and thanks again!

---

### Post by sandyd on 2010-06-13
> **eldonjr79 said:**
> Hey Carlee, or should I say 'master' ? :) 

I have tried this 'magical' line you've shown to me on my terminal. It works fine until I select LAMP and hit enter. Then nothing happens, it just skips to the next prompt. Am I supposed to do so on a Ubuntu server distro instead? 

Thanks for your invaluable info and advice!

I'm just a newbie web developer who just finished an introductory course and is trying to put everything into practice now by creating and managing my own website -- I already have some friends requests but no way I can make and maintain professional websites now.

Bye and thanks again!
ohh, soo sorry 'bout that.

your supposed to select the LAMP entry using your keyboard cursor, then press spacebar to select it. Then press tab to select "ok" and press enter.

---

### Post by eldonjr79 on 2010-06-13
aha! Now I got it! Thanks so much again Carlee!

Oh what a nice website you got btw!

see you,

---

