---
title: "No sound on youtube videos"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by sazan on 2009-10-31
Hi
I know this topic has been discussed before, but those solutions are not helping me now. 

I had my flash vidoes playing fine few days back and it doesnt seem to work now. 

I have upgraded the OS to 9.10. I downloaded the package again for adobe-flash and when i try to install it, i get following error

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.


What can be the problem? My firefox is updated.

---

### Post by yeats on 2009-10-31
Try the flashplugin-nonfree package instead.

---

### Post by connorh123 on 2009-10-31
Try typing in 
```
aumix
```
Then the first bar you'll see is like <Vol. Try using your arrows and point it all the way to the right. That might help.

---

### Post by sazan on 2009-10-31
Hi

Thanks for the replies.

But i am still getting the same error, I think i have to reinstall Flash plugin, but i am not able to achieve it. 

I keep getting the same error as i have mentioned for installing 'aumix' and flashplugin-nonfree package. 

Synaptic Manager didnt help either.

---

### Post by sazan on 2009-11-01
Anyone with some solution :(

---

### Post by JBAlaska on 2009-11-01
Open software sources and make sure you have "Software restricted by copyright or legal issues (multiverse) checked.

Then Open Package Manager and paste "flashplugin-installer" in the search box, then install it.

---

### Post by sazan on 2009-11-01
Problem solved from following command :

 dpkg --purge --force-all adobe-flashplugin

Thank you

---

### Post by gryall on 2009-11-01
The fix that worked for me is

got to applications=>sound and video => pulse audio volume control

There I discovered that ALSA plug in [firefox] was set to mute

---

### Post by norm7446 on 2009-11-01
By the Power of GOOGLE.

   I found this.....

      [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by arde on 2009-11-02
I had the same problem - i.e. no sound on youtube videos after upgrading to 9.10 (64-bit). Rhythmbox and totem played sound. Here is what worked for me:


[LIST=1]
[*]I purged flashplugin-nonfree and the flashplugin-installer from synaptic
[*]installed the adobe flash plugin 64-bit from the "Adobe labs" web site: [http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)
[*]Installed the swfdec-mozilla package from synaptic
[*]Voila!
[/LIST]

---

### Post by kennedyjch on 2009-11-22
> **gryall said:**
> The fix that worked for me is

got to applications=>sound and video => pulse audio volume control

There I discovered that ALSA plug in [firefox] was set to mute

This one worked for me (after installing the PulseAudio volume control) !!!!!! 

THANK YOU!!! :p

---

### Post by v8fusion on 2010-03-23
where do you place the libflashplayer.so file?

---

### Post by cmcanulty on 2010-04-21
I tried all that and still no sound though I could never find the ALSA plugin in the pulse audio-more details on that please. I hat not being able to hear any videos.

---

### Post by gazazello on 2010-05-07
I was working over adobeflashplayer (youtube, ...) missing sound for hours and found a simple but non-obvious solution.
I have two sound cards: internal Intel and external USB. I use usb (creative x-fi 5.1 surround), thus I turned off internal sound card with system sound preferences tool (just choosing "off" in dropdown in hardware tab for the specific sound card).
After installing the newest ALSA drivers and pulseaudio I encountered the problem of flashplayer sound absence, though rhythmbox produces sound in headphones. The problem was that Pulse is not default sound card interface, so some interference is happening. The solution is just to make Pulseaudio default. Here are steps:

create file /etc/asound.conf
put the following 6 lines inside of /etc/asound.conf :

pcm.!default {
type pulse
}
ctl.!default {
type pulse
}

Now logout/login. And done.

---

### Post by sag47 on 2010-05-17
I fixed it on Kubuntu 10.04.

It will likely work for Ubuntu as well.

Open a terminal, gnome-terminal in Ubuntu and konsole in Kubuntu.

Run alsamixer command while playing a youtube video and adjust the volume levels until you hear sound.  This also solved my [thread=1477942]skype troubles[/thread].

---

