---
title: "Installing RealPlayer"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by Peter Fjelstrup on 2009-03-14
When I downloaded RealPlayer, it stored itself in Desktop and not in Home, as advised. Then Terminal couldn't find it, when I ordered sudo chmod a+x RealPlayer*.
I was not allowed to move the file from Desktop to Home.
This is my first attempt to install .bin files into my system.

Also I couldn't activate 3rd level buttons (Alt GR) on the web, though it worked in OpenOffice.

Who can help me?
Peter

---

### Post by taurus on 2009-03-14
You don't have to move it to your $HOME.  You can leave it in ~/Desktop ($HOME/Desktop) as long as you know where it is.  From a terminal, try

```
cd ~/Desktop
chmod +x RealPlayer*
sudo ./RealPlayer*.bin
```

---

### Post by Peter Fjelstrup on 2009-03-15
> **taurus said:**
> You don't have to move it to your $HOME.  You can leave it in ~/Desktop ($HOME/Desktop) as long as you know where it is.  From a terminal, try

```
cd ~/Desktop
chmod +x RealPlayer*
sudo ./RealPlayer*.bin
```

I can't make the indefinite wawe ~ work in Terminal.
Is it nescessary or is it a substitute for a directory?
My path is Home/peter/Skrivebord (Desktop)
Why can't I make 3rd level grafic work?

---

### Post by SuperSonic4 on 2009-03-15
~ is a shortcut for /home/<user>

If instructions have code tags around them then they can be copy and pasted for the most part.

Have you checked your keyboard settings in KMenu -> System Settings -> Regional & Language

---

### Post by Peter Fjelstrup on 2009-03-15
> **SuperSonic4 said:**
> ~ is a shortcut for /home/<user>

If instructions have code tags around them then they can be copy and pasted for the most part.

Have you checked your keyboard settings in KMenu -> System Settings -> Regional & Language

RealPlayer installed. How you have to be accurate!
Where is KMenu?

---

### Post by kukibird1 on 2009-03-15
There is a .deb package in the Medibuntu repositories.
[http://packages.medibuntu.org/intrepid/realplayer.html](http://packages.medibuntu.org/intrepid/realplayer.html)

---

### Post by leonardo_neo on 2009-03-15
Go to the link below....

> [http://www.real.com/linux](http://www.real.com/linux)

Bottom right you will find the deb package option. Download that, double click the downloaded file, and voila! You are all set! :)

---

### Post by SunnyRabbiera on 2009-03-15
yeh use the .deb installer.
The one for medibuntu works pretty well too.

---

### Post by rburkartjo on 2009-03-15
peter, if there is a deb file avail for an application i want to install i also always use much easier

---

