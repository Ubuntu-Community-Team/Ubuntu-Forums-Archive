---
title: "Can't connect to certain sites on Firefox"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Imiimi on 2010-10-21
Hello

I can't connect to certain pages on Firefox. I usually get only the "Server not found" error, but just now after some updates it gave me this instead:

> XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.10/chrome/toolkit.jar!/content/global/netError.xhtml
Line Number 60, Column 12:    <title>&loadError.label;</title>
-----------^It's now back to "Server not found." Also, just to put it out there; the sites are working for everyone else.
I've also tried reinstalling Firefox through synaptic.

Thanks in advance.

---

### Post by cardamas on 2010-10-21
Have you fixed the problem? 
 
Thanks!!

---

### Post by seorangs on 2010-10-21
I have same problem, using firefox 3.6.10, then it's also have /tmp/ error when try to save file from internet

---

### Post by amjjawad on 2010-10-21
What exactly you guys are trying to open anyway?

---

### Post by mybconsulting on 2010-10-21
Hi, I have teh same prblem.
I've just open my URL  :  [http://localhost:943/admin](http://localhost:943/admin) and teh browser show me the follow error message:

Errore interpretazione XML: entità non definita
Indirizzo: jar:file:///usr/lib/firefox-3.6.10/chrome/toolkit.jar!/content/global/netError.xhtml
Linea numero 60, colonna 12:    <title>&loadError.label;</title>
-----------^
Thank you in advance!:popcorn:

---

### Post by openware on 2010-10-21
Same problem here!

---

### Post by amjjawad on 2010-10-21
Fellows, I still not sure what are you talking about :(
I'm using Firefox now with 5 or 6 active tabs and everything is fine.

Please, be more specific :)

---

### Post by Imiimi on 2010-10-21
I don't know how much more specific I should/could be?

Some sites refuse to load for me. That's it. They work for everyone else. 

And when I asked about it from my net provider they said everything connects alright on their end also.

One of the sites I can't connect to is:
[http://www.bluefairyint.com](http://www.bluefairyint.com)

It was fine just a couple days ago.

---

### Post by SeijiSensei on 2010-10-21
Start by forcing Firefox to recreate your user settings.  Close all instances of Firefox, then open a Terminal and enter the following at the "$" prompt:

```
cd .mozilla
mv firefox firefox.bad
```

Now start Firefox again and see if the problem still persists.  If it's gone, you can retrieve your bookmarks from the old installation with the Import tool in Organize Bookmarks.

Did you happen to load any add-ons for Firefox before this problem occurred?  Try removing all your extensions and see if the problem goes away.

If the problem still persists, probably the best thing to do is uninstall Firefox and re-install it.  

BTW, use Help > About and tell us the version of Firefox you're running.  Mine is at 3.6.10 on Maverick 10.10; I don't have a problem seeing the Blue Fairy site you posted.

---

### Post by amjjawad on 2010-10-21
> **Imiimi said:**
> I don't know how much more specific I should/could be?

Some sites refuse to load for me. That's it. They work for everyone else. 

And when I asked about it from my net provider they said everything connects alright on their end also.

One of the sites I can't connect to is:
[http://www.bluefairyint.com](http://www.bluefairyint.com)

It was fine just a couple days ago.

By providing examples of the websites that you're trying to access, that's all.
You need to understand that we're trying to help you but WE don't see your screen while YOU do :)

As you can see, I'm able to access your website so there's nothing wrong with that website, there's something wrong with your browser.

1) Go to Edit > Preferences > Privacy
Remove all cookies.

2) Close Firefox without saving any opened tabs

3) Restart your machine

4) Try to start firefox again and see if you could connect to these websites.

See attached.

[Useful Tips for you!]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by Imiimi on 2010-10-21
I'm on Lucid 10.04 and Firefox is v. 3.6.11

I've once tried to reinstall Firefox already and it didn't help, but I'll try one more time with your advice.

And yep, pretty much everybody else can connect there but me. xD

---

### Post by Imiimi on 2010-10-21
> **amjjawad said:**
> By providing examples of the websites that you're trying to access, that's all.
You need to understand that we're trying to help you but WE don't see your screen while YOU do :)

As you can see, I'm able to access your website so there's nothing wrong with that website, there's something wrong with your browser.

1) Go to Edit > Preferences > Privacy
Remove all cookies.

2) Close Firefox without saving any opened tabs

3) Restart your machine

4) Try to start firefox again and see if you could connect to these websites.

See attached.

[Useful Tips for you!]("http://ubuntuforums.org/showthread.php?t=1422475")


Yes, thank you. I've tried that too, didn't work... =( 
And sorry for not providing the site right away. I've just already confirmed with several other people that it works for them, so I was treating it as a fact.

---

### Post by Imiimi on 2010-10-21
Oh, and no new addons here, either. =(

---

### Post by amjjawad on 2010-10-21
> **Imiimi said:**
> Yes, thank you. I've tried that too, didn't work... =( 
And sorry for not providing the site right away. I've just already confirmed with several other people that it works for them, so I was treating it as a fact.

You welcome and it's okay, don't worry about it.

In my opinion, there's always plan B. I keep two browsers, actually I use two at the same time.

[Chrome]("http://www.google.com/chrome/eula.html?hl=en&brand=CHMB&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha&installdataindex=homepagepromo")
Try it and see if you could connect to your websites until you figure out what's wrong with Firefox.

---

### Post by Imiimi on 2010-10-21
Haha. Well this is encouraging. 

> Oops! Google Chrome could not find bluefairyint.comI'm beginning to fear that the problem really is on the net provider's end. As a last resort we grabbed a laptop with the same problem and accessed the site from a neighbouring house. It worked there. Net provider just keeps denying that anything's wrong.

---

### Post by amjjawad on 2010-10-21
> **Imiimi said:**
> Haha. Well this is encouraging. 

I'm beginning to fear that the problem really is on the net provider's end. As a last resort we grabbed a laptop with the same problem and accessed the site from a neighbouring house. It worked there. Net provider just keeps denying that anything's wrong.

Well at least you now know there is nothing wrong with your machine and most likely it's from your ISP.

---

### Post by Imiimi on 2010-10-21
Yep, thanks everyone. I'm taking this up with the net provider once more. 

They just won't listen, though.

---

### Post by SeijiSensei on 2010-10-21
Try editing /etc/resolv.conf (with sudo) and replace any nameserver entries you see with these lines 

```

nameserver 4.4.4.4
nameserver 8.8.8.8

```

Sounds like you have a DNS problem; these are Google's public servers.  Does that help?

---

### Post by Imiimi on 2010-10-21
> **SeijiSensei said:**
> Try editing /etc/resolv.conf (with sudo) and replace any nameserver entries you see with these lines 

```

nameserver 4.4.4.4
nameserver 8.8.8.8

```Sounds like you have a DNS problem; these are Google's public servers.  Does that help?
Didn't help. =( But thanks.

---

### Post by sepius on 2011-01-07
Did you fix the problem?, if so how?  I am having similar issue after a change to my network.  Put in new router (after removing temp router) and now some (like 2 or 3 out of the rest) web sites do not come up on one machine on the network (out of 4), it is running 10.04.

---

### Post by Imiimi on 2011-01-08
The problem got fixed eventually by itself. One day everything just worked again. So, I'm sorry but, I have no advice to share here.

---

### Post by amjjawad on 2011-01-08
> **Imiimi said:**
> **The problem got fixed eventually by itself**. One day everything just worked again. So, I'm sorry but, I have no advice to share here.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by kychot on 2011-03-03
The problem persist yet. It's not solved. I am using Firefox 3.6.13 (Ubuntu 10.4.):


The error message (in Czech) is:

Chyba parsování XML: Nedefinovaná entita
Adresa: jar:file:///usr/lib/firefox-3.6.13/chrome/toolkit.jar!/content/global/netError.xhtml
&#344;ádek 60, sloupec 12:    <title>&loadError.label;</title>
-----------^

This bug is described on:
[http://support.mozilla.com/cs/questions/767228](http://support.mozilla.com/cs/questions/767228)

But not solved yet as far as I know.

As I see the same problem was reported July 29, 2010  on ubuntu-bugs:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404963.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2404963.html)

[]("http://http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com")

---

### Post by Martinio on 2011-03-16
> **kychot said:**
> The problem persist yet. It's not solved. I am using Firefox 3.6.13 (Ubuntu 10.4.):


The error message (in Czech) is:

Chyba parsování XML: Nedefinovaná entita
Adresa: jar:file:///usr/lib/firefox-3.6.13/chrome/toolkit.jar!/content/global/netError.xhtml
&#344;ádek 60, sloupec 12:    <title>&loadError.label;</title>
-----------^


Hi kychot,

I upgraded to firefox-3.6.15 from 3.6.14 and started seeing the error.
 
I had to open a terminal and go to /usr/lib where I issued, ln -s firefox-3.6.15 firefox-3.6.14 (you need to use sudo).  If you want to get rid of the link use unlink <linkname>.

Good luck.

---

### Post by garolou on 2011-03-26
I confirm having the same problem. In the past I would just assume it was a problem at the web site.

```
XML Parsing Error: undefined entity
Location: jar:file:///usr/lib/firefox-3.6.15/chrome/browser.jar!/content/browser/certerror/aboutCertError.xhtml
Line Number 59, Column 12:
```

at this site: [https://lists.hcoop.net/listinfo/bond-users]("https://lists.hcoop.net/listinfo/bond-users")

If any one of you having this issue and using firefox 3.6.15, does visiting the above link also giving you trouble?

---

### Post by RadiantPhoenix on 2011-03-27
I was having the 'line 60, column 12' error, and I'm pretty sure it's an error in the 'problem loading page' screen.

I eventually realized that my error was occurring because Firefox had been updated but hadn't been restarted, and was looking for the page in a location that no longer existed. The fact that it got that far at all is pretty impressive.

The page still doesn't load, but it has the standard error screen now.

---

