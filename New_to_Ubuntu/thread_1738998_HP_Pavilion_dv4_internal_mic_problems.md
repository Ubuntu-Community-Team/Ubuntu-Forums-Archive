---
title: "HP Pavilion dv4 internal mic problems"
date: 2011-04-25
forum: New to Ubuntu
---

### Post by djyoung4 on 2011-04-25
So I have never been able to use the internal mic on my hp dv4 and I dont know why.  If I go to input under sound preferences there are no options and I cannot turn the volume up.  
[[img]http://ompldr.org/tOGYxNg[/img]](http://ompldr.org/vOGYxNg)
any ideas

---

### Post by djyoung4 on 2011-04-25
> **warttack said:**
> I recently found out how to get internal mic working, it works for dv4 models but im sure it work for some other models too, and its easier than i though.

**First:**Open the terminal and do "**killall -9 pulseaudio**" then uninstall pulseaudio and install esound "**sudo apt-get remove pulseaudio**" and "**sudo apt-get install esound**", restart your pc. 

**Second:**Now go to the menubar click on system then preferences then sound. On the Sound Preferences window change every set to HDA Intel using (alsa) or the equivalent to your "card/sound driver". On "Default Mixer Tracks" choose the **Device:** "**HDA Intel**" or equivalent for ur "card/sound driver". 

**Third:** Right click on the sound icon in gnome-panel and click in "**Open volume control**" in volume control "**Device:**" should be "**HDA Intel(Alsa Mixer)**". Click on Preferences button unmark all recording devices there and mark the "**Digital Input Source - Options**". Now back to the "Volume Control" Window you should have a tab Options click on it and select "Digital mic 1" or equivalent dont use "Analog Inputs". From now on you should have your mic working, to set the volume you can use the alsamixer tru the terminal, for the ones who doesnt know how to do it, just type "alsamixer" on terminal window.

**Fourth:** Please leave a comment reporting if working or not for you... or vote on poll in the top of the page.

HAVE A GREAT TIME WITH YOUR WORKING BUILT IN MIC. ;)
I tried this with no success.  I don't even get static

---

### Post by jeSah8ci on 2013-04-17
Did you get your problem fixed? I didn't have any issues until I upraded to Raring; I had originally installed pulseaudio when I had Quantal to be able to record some audio playback... but now that I have upgraded, I don't have any hardware listed for input recordings. Any tips as to what I should do?

Thanks in advance.

---

### Post by wildmanne39 on 2013-04-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

