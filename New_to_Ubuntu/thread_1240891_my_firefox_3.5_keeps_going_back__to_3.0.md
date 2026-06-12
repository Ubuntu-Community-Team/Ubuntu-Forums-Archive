---
title: "my firefox 3.5 keeps going back  to 3.0"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by blake7 on 2009-08-15
it keeps reverting back to 3.0 why and how can i stop it thank you

---

### Post by Lampi on 2009-08-15
I don't think it reverts, you might need to change the link /usr/bin/firefox to /usr/bin/firefox-3.5 - it points to firefox 3 if you don't change it:

```

sudo rm -vi /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
```

---

### Post by wojox on 2009-08-15
How are you launching it?

---

### Post by blake7 on 2009-08-15
I don't think it reverts, you might need to change the link /usr/bin/firefox to /usr/bin/firefox-3.5 - it points to firefox 3 if you don't change it.
--------------------------------------------------------------------------
errrr how do i change it??????
thank you

---

### Post by blake7 on 2009-08-15
does it matter where 3.5 is located
will that still work???

---

### Post by blake7 on 2009-08-15
can do i get 3.5 to start from my desttop????
i down loaded the file to my home file
 
thank you

---

### Post by 3rdalbum on 2009-08-15
> **blake7 said:**
> can do i get 3.5 to start from my desttop????
i down loaded the file to my home file
 
thank you

There's no need to do that; Firefox 3.5 is in the repositories. On Linux we use the software repositories wherever possible, rather than downloading programs off websites.

---

### Post by exsapientiasalus on 2009-08-15
You can install Firefox 3.5 from the command line (sudo apt-get install firefox-3.5) or from Synaptic. Just know that Firefox 3.0 can be removed, but considering it was added to the repos after Jaunty's launch, plugins such as sun-java6-plugin or gecko-mediaplayer can't be installed without dragging back Firefox 3.0. No problem really, just know that firefox (firefox-3.0) and firefox-3.5 will both exist in /usr/bin/. That being said, you'll need to launch Firefox 3.5 with the command Firefox-3.5. You can either make a custom launcher for the menu, use alt-f2, and so forth, but know that firefox will launch 3.0.

Someone else recommended deleting (or you could backup and rename) /usr/bin/firefox and then making a link named firefox that points to firefox-3.5, but each time a new Firefox 3.0 upgrade occurs, it will either overwrite your link. That's what I did, just be aware of the fact that it overwrites. I installed wajig and placed a hold on firefox so it won't upgrade, that way my link won't be overwritten. That's an idea to consider -- sudo apt-get install wajig && sudo wajig hold firefox-3.0.

---

### Post by blake7 on 2009-08-15
what the hell is it so complex

---

### Post by CatKiller on 2009-08-15
> **blake7 said:**
> what the hell is it so complex

It isn't.

```
sudo apt-get install firefox-3.5
```

Piece of piss.

You're making it far harder for yourself than you have to by insisting on installing things the Windows way.

---

### Post by colau on 2009-08-15
> **blake7 said:**
> what the hell is it so complex
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by blake7 on 2009-08-16
i did this sudo apt-get install firefox-3.5
what do i do now 
why cant it just load it self and work ???

cheers

---

### Post by CatKiller on 2009-08-16
> **blake7 said:**
>  what do i do now 

Step 1: Applications &#8594; Internet &#8594; Shiretoko web browser (this is Firefox 3.5)
Step 2: Browser the web.

---

### Post by XKCD64 on 2009-08-16
> **CatKiller said:**
> Step 1: Applications &#8594; Internet &#8594; Shiretoko web browser (this is Firefox 3.5)
Step 2: Browser the web.

Since the guy is a window user, he should drag it to the desktop and rename it to Firefox 3.5

:P

---

### Post by blake7 on 2009-08-16
great just done that wonderful

but as you can guess their is still not straight forward is it it has not loaded on my bookmarks scrapbook  plugin or anything

why could this not be done???

and yes how do i do it 

thank you for your time and iam sureyou find this as point less as i do

---

### Post by CatKiller on 2009-08-16
Firefox 3.5 from the repos will automatically pick up your Firefox 3.0 profile.

---

### Post by zer010 on 2009-08-16
I just got Shiretoko, now how do i remove firefox3.0?  Also, curiously, why is it called Shiretoko, and not Firefox3.5?  I'm split on what name I like better.:)

---

### Post by colau on 2009-08-16
> **zer010 said:**
> I just got Shiretoko, now how do i remove firefox3.0?  Also, curiously, why is it called Shiretoko, and not Firefox3.5?  I'm split on what name I like better.:)
[shiretoko]("http://www.rebelzero.com/ubuntu/ubuntu-9-04-and-firefox-3-5-shiretoko/162")

---

### Post by zer010 on 2009-08-17
So... I can't remove FF3.0?  Just make a bunch of links and patches?  Is it that FF3.5 isn't a stand-alone app on 9.04?

---

### Post by CatKiller on 2009-08-17
> **zer010 said:**
> So... I can't remove FF3.0?

Of course you can. ```
sudo apt-get remove firefox-3.0
```

---

### Post by blake7 on 2009-10-26
hi i have a 16gb class 6 sd card(that i got of ebay)  and i have saved on to it a nubmer of avi files
but now when i come to play them ( from the card or if i have put them back on to my main hard drive) they dont play

when i load the file it now says

Could not determine type of stream

is thier anything i can do 

thank you

---

