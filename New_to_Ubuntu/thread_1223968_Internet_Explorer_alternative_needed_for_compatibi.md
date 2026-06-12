---
title: "Internet Explorer alternative needed for compatibility"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by Volume on 2009-07-26
I have a website for school for which FF 3.0 will not work, and I must use IE it says.  I don't have a Windblows system up right now, and I really need to be able to access this site.  Are there any browsers out the for Linux for this sort of situation?

Steve

---

### Post by c0mput3r_n3rD on 2009-07-26
You can install wine;
```

sudo apt-get install wine

```
And then install IE for wine (google that).

I think that's your only option.

---

### Post by aesis05401 on 2009-07-26
Check out ietab.

---

### Post by steveneddy on 2009-07-26
> **aesis05401 said:**
> Check out ietab.

IEtab only works on Firefox running on Windows.

Try a User Agent Switcher.

It will tell a web site that you access with Firefox/Linux that you are on IE/Windows

Very cool tool.

LINKY:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

EDIT:

Here's a list you can DL that adds more user agents to the list:

[http://www1.qainsight.net:8080/2007/03/04/Update+To+User+Agent+Import+For+User+Agent+Switcher.aspx](http://www1.qainsight.net:8080/2007/03/04/Update+To+User+Agent+Import+For+User+Agent+Switcher.aspx)

---

### Post by cybergalvez on 2009-07-26
> **steveneddy said:**
> IEtab only works on Firefox running on Windows.

Try a User Agent Switcher.

It will tell a web site that you access with Firefox/Linux that you are on IE/Windows

Very cool tool.

LINKY:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Agreed use agent switcher to set your FF browser to report that its IE, in all likely-hood it will work fine

---

### Post by c0mput3r_n3rD on 2009-07-26
> **steveneddy said:**
> IEtab only works on Firefox running on Windows.

Try a User Agent Switcher.

It will tell a web site that you access with Firefox/Linux that you are on IE/Windows

Very cool tool.

LINKY:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

That is a really cool tool! I just installed it even though I have no use for it now. :-D

---

### Post by Volume on 2009-07-26
Me too!  I don't have any use for it on my PC, but my wife really needs it!  Awesome tip dude!  ThankS!

---

### Post by Volume on 2009-07-26
Just had a minor heart attack, I finally sold Ubuntu to my wife, got done installing it, finished patting myself on the back, and then she says "How do I install IE"?  SLAP! I nearly fainted...  Great app

---

### Post by steveneddy on 2009-07-26
> **Volume said:**
> Just had a minor heart attack, I finally sold Ubuntu to my wife, got done installing it, finished patting myself on the back, and then she says "How do I install IE"?  SLAP! I nearly fainted...  Great app

You could also install VirtualBox (3.0 from the web site) and use that to install Windows on your machine and just fire up Windows when you need it.

I do that and have XP and Vista installed and just start them when necessary to get work done.

There is even a seamless mode to have both on the desktop at the same time.

Notice in the screenshot there is the Gnome desktop with an XP bar over the Gnome bottom bar. There are also two Windows apps, Control panel and My Computer running. You can use both at the same time on the same desktop. Really easy to get work done.

---

### Post by mikechant on 2009-07-27
If you use "ies4linux" this gives you a simple way to get IE6 installed and running. I know IE6 is old and rubbish but if it works with the site you need, and it's just for use on that one site, this could be the easiest way.

Here's a ubuntu howto:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by halovivek on 2009-07-27
I am using ies4linux it is doing good and fine. it is really a wonderful one.

---

### Post by Troll_the_Great on 2009-07-27
> **steveneddy said:**
> IEtab only works on Firefox running on Windows.

Try a User Agent Switcher.

It will tell a web site that you access with Firefox/Linux that you are on IE/Windows

Very cool tool.

LINKY:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

EDIT:

Here's a list you can DL that adds more user agents to the list:

[http://www1.qainsight.net:8080/2007/03/04/Update+To+User+Agent+Import+For+User+Agent+Switcher.aspx](http://www1.qainsight.net:8080/2007/03/04/Update+To+User+Agent+Import+For+User+Agent+Switcher.aspx)

Maybe this is a silly question, but how do I import the list above, so I can have more user agents?

---

### Post by LookTJ on 2009-07-27
> **Troll_the_Great said:**
> Maybe this is a silly question, but how do I import the list above, so I can have more user agents?
Tools -> Default User Agent -> Edit User Agents -> import and then import the file you have

To download an xml file, you need to right click and click save link/page as.

:)

---

### Post by Troll_the_Great on 2009-07-27
> **LookTJ said:**
> Tools -> Default User Agent -> Edit User Agents -> import and then import the file you have

To download an xml file, you need to right click and click save link/page as.

:)

Thx allot, it worked!

---

