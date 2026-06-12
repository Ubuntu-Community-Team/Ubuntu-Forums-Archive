---
title: "Issues installing wine"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by wagg4 on 2009-06-22
I used to have Xp but thought ubuntu was a good system so i installed ubuntu over because i had heared of WINE. Basically i run v 9.04 and have followed the instructions but get"Can not install 'wine' (E:Unable to correct problems, you have held broken packages.)" 

This is the only thing i have downloaded exept updates.  Any help on how to get this to work? Thanks

---

### Post by ad_267 on 2009-06-22
Can you post the exact error message? Maybe post the output of "sudo apt-get update && sudo apt-get upgrade"

---

### Post by lisati on 2009-06-22
You might want to try the following from the command line (Applications->Accesories->Terminal) and then rety installing Wine:
```
sudo dpkg --configure -a
```
It will ask for your password: don't worry if it doesn't show, just tpye it in as normal.

---

### Post by nothingspecial on 2009-06-22
```
sudo apt-get install -f
```

To fix broken packages

---

### Post by wagg4 on 2009-06-22
ok i can download it but when i get to package installer i get an error that says "Dependency is not satisfiable: libasound2" ???:confused:

---

### Post by Bradtek on 2009-06-22
Install the missing dependency

```
sudo apt-get install libasound2
```

Or search for it in Synaptic

---

### Post by 3rdalbum on 2009-06-22
> you have held broken packages.

Go into Synaptic Package Manager. Click "Custom Filters" in the bottom-left corner of the window, and then Broken in the left pane. Anything that is listed as "broken" you should either remove or try to reinstall.

Your package management system will not work if you have broken packages.

---

### Post by wagg4 on 2009-06-22
> sudo apt-get install libasound2

[http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Screenshot-mattmatt-laptop.png](http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Screenshot-mattmatt-laptop.png) 

this is what i get

---

### Post by wagg4 on 2009-06-22
> **3rdalbum said:**
> Go into Synaptic Package Manager. Click "Custom Filters" in the bottom-left corner of the window, and then Broken in the left pane. Anything that is listed as "broken" you should either remove or try to reinstall.

Your package management system will not work if you have broken packages.

it says there are none broken?

---

### Post by nothingspecial on 2009-06-22
I looks like your fixed, try to install wine again.

---

### Post by Bölvaður on 2009-06-22
> **wagg4 said:**
> ok i can download it but when i get to package installer i get an error that says "Dependency is not satisfiable: libasound2" ???:confused:
FAIL.

Do not try to go to websites to download any form of installers and then try to install them after downloading.
Use the wonderful package managers that will make sure you have all the dependencies.. otherwise you could just as well be (perhaps you are) compiling from source.

To install wine just :[URL="apt:wine"]
sudo apt-get install wine[/URL]
or find it under Add/Remove

If you want the latest version go to the [winehq]("http://ubuntuforums.org/www.winehq.org") website and follow the information on how to add their repos to your third party repositories and add an autentication key to make sure it hasnt been fittled with by untrusted sources (which is as risky as getting random installers from [random] websites).

---

### Post by wagg4 on 2009-06-22
It still says the same thing :(

---

### Post by wagg4 on 2009-06-22
> **Bölvaður said:**
> FAIL.

Do not try to go to websites to download any form of installers and then try to install them after downloading.
Use the wonderful package managers that will make sure you have all the dependencies.. otherwise you could just as well be (perhaps you are) compiling from source.

To install wine just :[URL="apt:wine"]
sudo apt-get install wine[/URL]
or find it under Add/Remove

If you want the latest version go to the [winehq]("http://ubuntuforums.org/www.winehq.org") website and follow the information on how to add their repos to your third party repositories and add an autentication key to make sure it hasnt been fittled with by untrusted sources (which is as risky as getting random installers from [random] websites).

that just gives me the package broken message that i had at the start

---

### Post by wagg4 on 2009-06-22
just to check what have i done this right : [http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Help2.png](http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Help2.png)

---

### Post by SunnyRabbiera on 2009-06-22
> **wagg4 said:**
> just to check what have i done this right : [http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Help2.png](http://s913.photobucket.com/albums/ac339/wagg4/?action=view&current=Help2.png)

The repositories look right to me, but I am wondering what the error is about.
How did you try to install wine originally?

---

### Post by wagg4 on 2009-06-22
just uding the link [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by SunnyRabbiera on 2009-06-22
> **wagg4 said:**
> just uding the link [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

and you didnt use the "install older .deb" link correct?
This one:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

Just doing some detective work here, but it might help in your issue...
Not saying it will though -.-;;

---

### Post by wagg4 on 2009-06-22
have tried them they gave me > Dependency is not satisfiable: libasound2 the one of the tut page gives me the message >  Can not install 'wine' (E:Unable to correct problems, you have held broken packages.) 

---

### Post by SunnyRabbiera on 2009-06-22
> **wagg4 said:**
> have tried them they gave me  the one of the tut page gives me the message

So is that the method your tried originally, by downloading from that page?
Just trying to understand what you did here, so I can possibly help you.

---

### Post by wagg4 on 2009-06-22
i tries that methos origianly becasue i t wont download from the tutorial page

---

### Post by SunnyRabbiera on 2009-06-22
> **wagg4 said:**
> i tries that methos origianly becasue i t wont download from the tutorial page

Alright, yeh you got to abandon the windows way of thinking when installing a application on Linux.
You got you repositories set, thats a great start.
I say ignore the packages you downloaded, they wont do no good.
The best way to learn how to install most applications is to take a look here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

That should get you the jist of using what are called package managers.
Unlike windows where you go to website A, B or C to get software package managers offer a gateway to installable apps.
There is a learning curve here however, but its not that steep with good help :D

---

### Post by wagg4 on 2009-06-22
basicaly all the ways that have been sugested wont work. How can i get wine to install?

---

### Post by wagg4 on 2009-06-22
The error i get is > Can not install 'wine' (E:Unable to correct problems, you have held broken packages.) 



---

### Post by wagg4 on 2009-06-22
Ok :) i got wine to work and install after following instructions on the spotify website [http://www.spotify.com/en/help/faq/wine/](http://www.spotify.com/en/help/faq/wine/) 

administrators close this thread plz :)

---

### Post by wagg4 on 2009-06-22
I love ubuntu!! :) (AND DONT FORGET WONDERFULL WINE! :) I AM THE HAPPIEST PERSON EVER :D

---

### Post by goog64 on 2009-06-27
Today, when trying to install Wine, I got the same error message as wagg4:
"Dependency is not satisfiable: libasound2"

**BUT** I have successfully installed Ubuntu and wine 5 times on my laptop during the past 3 days (don't ask why I did this!). I did it exactly the same way each time, but now I get the error. This is pretty frustrating for a complete noob like me who has no idea what's going on.

---

