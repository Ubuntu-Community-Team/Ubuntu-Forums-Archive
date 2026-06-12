---
title: "What do you recommend to watch dvd's"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by johndingli on 2008-12-14
Can someone help me in what should i install to watch dvd's thanks

---

### Post by adobrakic on 2008-12-14
I use VLC, and it works perfectly.

---

### Post by taurus on 2008-12-14
VLC.

```
sudo apt-get update
sudo apt-get install vlc
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by adobrakic on 2008-12-14
Also, might wanna check this thread out:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by johndingli on 2008-12-14
Thanks for your prompt response i will try vlc

---

### Post by linuxguymarshall on 2008-12-14
Yes VLC. I know you don't need anything extra on Windows but I think you need to install the libdvd(?) file on linux. I have had mine configured so long I do not know.

---

### Post by adobrakic on 2008-12-14
Shouldn't install via terminal or synaptic get all the dependencies?

---

### Post by LowSky on 2008-12-14
> **linuxguymarshall said:**
> Yes VLC. I know you don't need anything extra on Windows but I think you need to install the libdvd(?) file on linux. I have had mine configured so long I do not know.

Actually Windows XP cannot play DVDs natively. You need codec support from a program like PowerDVD

---

### Post by MenZa on 2008-12-14
> **adobrakic said:**
> Shouldn't install via terminal or synaptic get all the dependencies?

Yup. Although I think he may be talking about libdvdcss2, which is required to watch some encrypted DVDs.

Otherwise, try installing the ubuntu-restricted-extras:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by frank002 on 2008-12-14
You are correct. First install the medibuntu repository ,then open Synaptic and install libdvdcss3. You should be able to watch dvds. If you have not installed the medibuntu rep, go to the following page    [http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html).

---

### Post by johndingli on 2008-12-14
I installed vlc and all the required codecs you told me but now i have a problem with sound.No sound in playback

---

### Post by richg on 2008-12-14
I have been following this thread as I cannot view DVD movies with VLC so far.
I went to Synaptic Package Manager and downloaded VLC. I then installed ubuntu-restricted-extras.
Still no results. Is there a step by step list of required actions to view DVD movies in 8.04, not links to other threads for this issue which usually have more links but a single step by step list for 8.04 or even 8.10.
The original question did not define which version of Ubuntu.
Thanks.

Rich

Success. I was not using VLC correctly. Good video and audio. Thanks for suggestions.

---

### Post by philinux on 2008-12-14
System>prefs sound. Do you get sound when clicking test.

You could try changing from auto to pulse or alsa. See if sound appears on dvd.

---

### Post by oldos2er on 2008-12-14
> **richg said:**
> I have been following this thread as I cannot view DVD movies with VLC so far.
I went to Synaptic Package Manager and downloaded VLC. I then installed ubuntu-restricted-extras.
Still no results. 
Rich

 You first need to enable the Medibuntu repository for your version of Ubuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

 Then run this command in a terminal:

 sudo apt-get update && sudo apt-get install libdvdcss2

---

### Post by richg on 2008-12-14
Thanks, but I had done that also. I just forgot to mention it. I got VLC to see a video once. Now I cannot figure out how I managed to view the video so back to square one.

Still looking for a single list of steps to accomplish this with 8.04 and 8.10. No links which usually lead to more links and questions.

Just a step by step list would be very nice for setting up to use VLC. That should not be too hard.

Rich

---

