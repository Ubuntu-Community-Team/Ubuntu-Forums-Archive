---
title: "Blank Screen after Logging in Ubuntu 11.04?"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by courage1919 on 2011-08-12
So, I did a fresh reinstall of Ubuntu 11.04. When I login from the login screen at startup, I just get a total blank screen of the desktop. I've waited there for hours and still nothing is there, just a blank screen of the desktop. What's wrong?

P.S. My computer is a Dell Optiplex GX270.

---

### Post by androssofer on 2011-08-12
> **courage1919 said:**
> So, I did a fresh reinstall of Ubuntu 11.04. When I login from the login screen at startup, I just get a total blank screen of the desktop. I've waited there for hours and still nothing is there, just a blank screen of the desktop. What's wrong?

P.S. My computer is an Optiplex GX270.

if u do: 

ctrl  alt  F1

what happens?

---

### Post by courage1919 on 2011-08-12
Hm, it seems that when i just login to ubuntu now, i get an error saying:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."

---

### Post by androssofer on 2011-08-12
> **courage1919 said:**
> Hm, it seems that when i just login to ubuntu now, i get an error saying:

"It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment."

hummm. could select the gnome trad option, then check u hav all ur graphics drivers installed(nvidia, ati etc...). then select unity once they r in and it shud work. or if tht doesnt work / its a old comp, install unity 2d. and try tht? 

:-)

---

### Post by courage1919 on 2011-08-12
> **androssofer said:**
> hummm. could select the gnome trad option
Where do I find that?

Here's what the message looks like:

[IMG]http://i620.photobucket.com/albums/tt281/kintahkuntay404/IMG_0034.jpg[/IMG]

Also, when I login through ubuntu, it just lets me login now without the choppy sound of the drums anymore.

---

### Post by androssofer on 2011-08-12
> **courage1919 said:**
> Where do I find that?

interestingly not the 1st time this has been asked today...

on your login screen in a menu at the bottom that lets you choose the session. choose "Gnome class desktop".

this is an image of the menu:

[http://cloud.addictivetips.com/wp-content/uploads/2011/03/Login_thumb.png](http://cloud.addictivetips.com/wp-content/uploads/2011/03/Login_thumb.png)

note: (learnt this from another post): if it the task bar is missing from the bottom of the screen, click below the screen where u rekon it shud b.. usually works :-)

---

### Post by courage1919 on 2011-08-12
lol please excuse my noob actions because I'm still trying to learn everything in ubuntu! ^_^

ok, once I do that, I follow your 2nd post?

---

### Post by courage1919 on 2011-08-12
There's no unity 2D!! :O

---

### Post by androssofer on 2011-08-12
> **courage1919 said:**
> lol please excuse my noob actions because I'm still trying to learn everything in ubuntu! ^_^

ok, once I do that, I follow your 2nd post?

thts y its called absolute beginners talk ;-)

so on the login, select "gnome classic desktop". then wen tht loads go to adiitional drivers:

System >> admin >> additional drivers

and install any drivers that it recommends for your graphics card. then restart and on the login screen select "ubuntu desktop edition" and u'll have unity :-). 

if there are no drivers in additional drivers. then open the software center. 

applications >> software center

and search for "unity" then select unitu 2D and install it.

then retart and when the login screen loads, unity 2d will be in ur menu :-)

now u hav unity!

or if ur happy with gnome classic, just select it during login and ur done...

---

### Post by courage1919 on 2011-08-12
Hmm, not sure what I'm suppose to do from here. :/

[IMG]http://i620.photobucket.com/albums/tt281/kintahkuntay404/IMG_0036.jpg[/IMG]

---

### Post by androssofer on 2011-08-15
> **courage1919 said:**
> Hmm, not sure what I'm suppose to do from here. :/

[IMG]http://i620.photobucket.com/albums/tt281/kintahkuntay404/IMG_0036.jpg[/IMG]

sorry for the delay... crazy weekend :-).

anyway, read into the issue a bit. apparently its an issue with the driver installer.

here is the solution:

> I had the same problem. I removed all nvidia drivers with Synaptic. Then I installed again from command line - sudo apt-get install nvidia-current and ran sudo nvidia-xconfig and it worked.

so open up synaptic package manager:

system >> admin >> synaptic package manager

then search for "nvidia" and look for the driver from the screen shot. and remove it. then do:

```
sudo apt-get install nvidia-current
```

then:

```
sudo nvidia-xconfig
```

***note**: this isnt my solution and i have nvr tested it, so cant guarantee it will work.

---

### Post by EScout209 on 2013-01-16
I’m having a similar problem with 12.10.  I installed it fresh beside Windows XP Pro.  I installed it on a Dell Inspiron 600m, using the instructions found here [http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html](http://www.webupd8.org/2012/11/how-to-install-ubuntu-1210-on-non-pae.html) (It has a non-PAE processor) It has an ATI video card (Mobility Radeon 9000)  What I find odd is that I have a bunch of usable controls in the upper right edge of the log in screen, which disappear once I log in.

---

