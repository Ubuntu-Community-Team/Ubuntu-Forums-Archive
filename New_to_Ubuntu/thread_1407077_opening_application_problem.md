---
title: "opening application problem"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by soccersnowboarder on 2010-02-14
I have a problem opening games, and somethings that i have downloaded. Some of these include, google earth which i got through medibuntu, and games such as openarena, i tried downloading random games such as "extreme tux racer" but that would not work to.  I updated to Ubuntu 9.10, and have had the problem since. I have tried reinstalling the games it didn't work. I downloaded medibuntu for the first time AFTER the upgrade. I thought it could be a problem with 3D accelerator, so when i tried to download that under Ubuntu software center, it downloaded but then said  I also had a video card which i removed, after the upgrade, and after the problems, which i then removed, then added again because it stopped working, and then worked again later. "Could not detect any configurable direct-rendering capable devices. DRIconf will be started in expert mode."and i do not know what to do from there. beginner talking please answer

---

### Post by Muzer on 2010-02-14
What is your graphics card?

If you don't know, post the output of lspci -nn | grep VGA

---

### Post by soccersnowboarder on 2010-02-14
GE force 8500 GT

---

### Post by sandyd on 2010-02-14
> **soccersnowboarder said:**
> GE force 8500 GT

I, unforunately cant care enough to read through a huge block of text
So you installed the drivers through the hardware drivers thingy right?

download your graphics card here : [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

save it to the desktop.
press ALT+F1 to flop over to a virtual terminal
login.
type.this.in.
```

sudo chmod 777 ~/Desktop/nvidia*
sudo sh ~/Desktop/nvidia*

```

---

### Post by soccersnowboarder on 2010-02-19
it wont let me open this.. i downloaded it and when i try to open it it says, "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again." when i try to open it... when i try to open it through terminal it says it can't open it... i have a Geforce 8500 GT please help it keeps not allowing me to open more and mmore applications!1

---

