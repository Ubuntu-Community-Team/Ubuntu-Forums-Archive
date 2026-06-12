---
title: "sound driver"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2010-08-10
can anyone tell me how to reinstall sound driver in ubuntu 9.10???

---

### Post by Sylos on 2010-08-10
Hello.

This depends on which drivers you are using for the sound (oss, alsa, pulseaudio) etc.

Can you elaborate on the problem a bit.

---

### Post by viditgoyal3009 on 2010-08-10
> **Sylos said:**
> Hello.

This depends on which drivers you are using for the sound (oss, alsa, pulseaudio) etc.

Can you elaborate on the problem a bit.
pulse-audio

my laptop is hp mini 110
intel atom processor
1gb ram, intel chipset

---

### Post by Sylos on 2010-08-10
Thanks.

Ordinarily you would use something like

```
sudo apt-get install pulseaudio
```

However, if the driver has simply stopped working you'll probabbly get a message saying that its already installed. In which case try 

```
sudo apt-get purge --remove pulseaudio
```

then..

```
sudo apt-get install pulseaudio
```

Post back if you get issues.

---

### Post by viditgoyal3009 on 2010-08-10
thanks will definitely try it but there is one more problem, i recently installed a belkins router g series at my home. When i try to connect internet using it, it keeps on asking for network password. Inspite of providing it several times, i am still unable to connect internet using router which happens to work absolutely fine on windows 7.. 
Please help

---

### Post by Sylos on 2010-08-10
Im afraid I have no idea when it comes to wireless/router issues. I suggest you create a new thread for that. Your current thread title of 'Sound issues' probabbly wont atrract the people with the best knowledge.

---

### Post by Kafubie on 2010-08-10
> **viditgoyal3009 said:**
> thanks will definitely try it but there is one more problem, i recently installed a belkins router g series at my home. When i try to connect internet using it, it keeps on asking for network password. Inspite of providing it several times, i am still unable to connect internet using router which happens to work absolutely fine on windows 7.. 
Please help

Check your Belkin router settings by going to your private IP.
If you are sure you didn't set it as a different one.
[http://192.168.2.1/](http://192.168.2.1/)
You have to check on a different computer that is connected to the network.

Or..  Restart the router.

I have a Belkin router and a Hp Mini.  lolio

Hope this helped. :D

---

### Post by viditgoyal3009 on 2010-08-13
> **Sylos said:**
> Thanks.

Ordinarily you would use something like

```
sudo apt-get install pulseaudio
```

However, if the driver has simply stopped working you'll probabbly get a message saying that its already installed. In which case try 

```
sudo apt-get purge --remove pulseaudio
```

then..

```
sudo apt-get install pulseaudio
```

Post back if you get issues.
it didnt work...wat r other options??

---

### Post by lidex on 2010-08-13
> **viditgoyal3009 said:**
> it didnt work...wat r other options??
Re-installing may not be the answer, but to re-install alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**Reboot.**
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

---

