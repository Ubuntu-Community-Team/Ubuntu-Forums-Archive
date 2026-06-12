---
title: "Iexplorer"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-21
Hello to all.
I need to work with internet explorer 7 or later on Ubuntu. The reason is that my bank accepts only IE for internet banking.
I had done it before with WINE in ubuntu 10.something , but now seems more complicated. Even I installed WINE and IE it didnt worked at all. I had a banch of errors like can not find the site etc. Any alternative idea?
Thank you!

---

### Post by An Sanct on 2011-08-21
> **vagelism said:**
> Hello to all.
I need to work with internet explorer 7 or later on Ubuntu. The reason is that my bank accepts only IE for internet banking.
I had done it before with WINE in ubuntu 10.something , but now seems more complicated. Even I installed WINE and IE it didnt worked at all. I had a banch of errors like can not find the site etc. Any alternative idea?
Thank you!

I personally would check if they just check the string your browser identifies with (MS update did not let you update from non IE browsers ... It might have changed now)

So check for tools to modify your Browser ID (also called a User Agent)

(mine is: *Mozilla/5.0 (X11; Linux x86_64; rv:9.0a1) Gecko/20110819 Firefox/9.0a1*)

edit: I found the addon for firefox ... [here]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")

---

### Post by snip3r8 on 2011-08-21
Personally what I would do if my bank ONLY accepted IE ,which i dont even want to use when im in windows (i prefer firefox). I would tell them to either move with the times or i'll find another bank.

My bank supports all browsers...

---

### Post by An Sanct on 2011-08-21
> **snip3r8 said:**
> Personally what I would do if my bank ONLY accepted IE ,which i dont even want to use when im in windows (i prefer firefox). I would tell them to either move with the times or i'll find another bank.

 

My bank supports all browsers...

Yes, we would all like to do something like that with our beloved banks ... but its a hassle, so an User Agent switching solution should just do it ... ;)

---

### Post by vagelism on 2011-08-21
> **An Sanct said:**
> I personally would check if they just check the string your browser identifies with (MS update did not let you update from non IE browsers ... It might have changed now)

So check for tools to modify your Browser ID (also called a User Agent)

(mine is: *Mozilla/5.0 (X11; Linux x86_64; rv:9.0a1) Gecko/20110819 Firefox/9.0a1*)

edit: I found the addon for firefox ... [here]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")

Unfortunately is not working!

---

### Post by mike555 on 2011-08-21
When you talk to your bank send them to this link , it shows IE is very low % of users;   [http://www.w3schools.com/browsers/browsers_stats.asp](http://www.w3schools.com/browsers/browsers_stats.asp)

---

### Post by An Sanct on 2011-08-21
> **vagelism said:**
> Unfortunately is not working!

What is not working? Does the addon not want to install or does the bank want to have some silly ocx/dll stuff on your computer?

(An over-bloated alternative is to install Windows in VirtualBox ...)

---

### Post by ixtok on 2011-08-21
Try VirtualBox. You can get it in the software center. It should run IE and almost everything else windoz wize.

---

### Post by vagelism on 2011-08-21
> **An Sanct said:**
> What is not working? Does the addon not want to install or does the bank want to have some silly ocx/dll stuff on your computer?

(An over-bloated alternative is to install Windows in VirtualBox ...)

No it is not!
When I login after a while it kick me out when i click in any menu!

---

### Post by An Sanct on 2011-08-21
Did you install the addon and selected Internet Explorer from the tools menu?

[You can confirm the User Agent string here]("http://show-ip.net/browserinfo/")

---

### Post by vagelism on 2011-08-21
> **An Sanct said:**
> Did you install the addon and selected Internet Explorer from the tools menu?

[You can confirm the User Agent string here]("http://show-ip.net/browserinfo/")

Yes I did. I also did the same in chrome... nothing.
Now I am downloading the Virtualbox. I hope it will work with explorer!
Thank you!

---

### Post by An Sanct on 2011-08-21
For VirtualBox you need a windows installation CD. It is a Virtual Machine.

---

### Post by in·ter·punct on 2011-08-21
Try one of these:

[LIST]
[*][Linie]("https://code.google.com/p/linie/") has support for IE7.
[*][playonlinux]("http://www.playonlinux.com/en") has support for IE7.
[*][IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") has beta support for IE7+.
[/LIST]

---

