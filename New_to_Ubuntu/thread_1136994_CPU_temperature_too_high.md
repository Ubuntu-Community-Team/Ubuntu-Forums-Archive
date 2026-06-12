---
title: "CPU temperature too high"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by erunamo114 on 2009-04-25
Hey guys. I am running Ubuntu Intrepid 8.10, and I recently downloaded and configured the lmsensors app from the repositories. I have two questions.

1.) There are several different sensors displayed on the task panel, and I am not sure what each temperature gauge label means. They are labeled as "CUP", "temp1", "Core0", "Core1", another "temp1", "temp2", and "GPU". Could someone tell me what each of those are telling me the temperature of?

2.) MOst of the gauges are seeming to run consistently high. Once my computer has been running for about 10-20 minutes the lowest temperature out of the ones listed above is 40 degrees C. The GPU is actually running at 76 degrees right now which is way too high. Anyone have any suggestions of how to lower the temperature of these? I've tried just dusting out my desktop on the inside and everything. I know that the GPU is probably the video card, but I am currently not running any video at all so I have no idea why it's that high. Any suggestions would be much appreciated. Thanks!

---

### Post by pbpersson on 2009-04-25
[http://www.lm-sensors.org/wiki/FAQ/Chapter1#WhatsensorsareavailableonmyPC]("http://www.lm-sensors.org/wiki/FAQ/Chapter1#WhatsensorsareavailableonmyPC")

---

### Post by cubeist on 2009-04-25
well you need to tell us what hardware you are using, and how you are using it.  Those temps are not unheard of... For example, I am running an OC AMD and it idles at 36 to 38 Centigrade, and my GPU (ATI) idles at 46 C.

The problem with lm-sensors is sometimes there are incorrect multipliers, so the temps are not accurate, and sometimes it will incorrectly list things as other things.  That gpu temp might be incorrectly reporting an electrical component on the board.

My advice is to check you temps in bios first to see if sensors is accurate.

---

### Post by kansasnoob on 2009-04-25
I just use computertemp because I have only a CPU temp monitor, but when I'm running too hot I look in System > Administration > System Monitor (Processes Tab) and see what's running at what %.

---

### Post by presence1960 on 2009-04-25
> **erunamo114 said:**
> Hey guys. I am running Ubuntu Intrepid 8.10, and I recently downloaded and configured the lmsensors app from the repositories. I have two questions.

1.) There are several different sensors displayed on the task panel, and I am not sure what each temperature gauge label means. They are labeled as "CUP", "temp1", "Core0", "Core1", another "temp1", "temp2", and "GPU". Could someone tell me what each of those are telling me the temperature of?

2.) MOst of the gauges are seeming to run consistently high. Once my computer has been running for about 10-20 minutes the lowest temperature out of the ones listed above is 40 degrees C. The GPU is actually running at 76 degrees right now which is way too high. Anyone have any suggestions of how to lower the temperature of these? I've tried just dusting out my desktop on the inside and everything. I know that the GPU is probably the video card, but I am currently not running any video at all so I have no idea why it's that high. Any suggestions would be much appreciated. Thanks!

did you try sensors-applet in Synaptic. Once installed add it to your panel by right clicking a panel and choosing "add to panel". Choose Hardware Sensors Monitor in the choices. Select which sensors you want displayed in preferences by right clicking the display in the panel, some do display incorrect values. Unless you have had an overheating problem prior just don't select the "out of whack" ones to be displayed. I did double check my CPU readings in my BIOS also to be sure.

---

