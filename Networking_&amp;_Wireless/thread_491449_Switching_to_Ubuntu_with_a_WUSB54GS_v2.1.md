---
title: "Switching to Ubuntu with a WUSB54GS v2.1"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by Wickens on 2007-07-03
So far I'm getting nowhere. I've already read the guide on these forums for this specific device. ([http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs+2.1]("http://ubuntuforums.org/showthread.php?t=225206&highlight=wusb54gs+2.1"))
And it's done nothing but confuse me.
On step 1 it says:
cpp is already the newest version
gcc is already the newest version
E: Couldn't find package build-essential
I've been using windows for a LONG time and I decided to make the switch but none of the commands I'm told to use in the terminal are working. I'm in the correct directory as it states in the guide but nothing is working.
If anyone can help me I'd appreciate it, I WANT to use linux but it seems to be forcing me back to windows because I have a huge migraine from this crap.

---

### Post by Wickens on 2007-07-03
Back to windows for me it seems. I'm not going to sit on my laptop with a blank ubuntu screen any longer.

---

### Post by md2020 on 2007-07-03
Sorry I couldn't reply earlier. I have the same wireless USB as you. And as I write this and post I am doing it through its connection. So it will work. But I do feel your pain, I was not able to follow the instructions by the letter to get mine working either. I had issues on step 1 as well.

Though I am pretty new to Ubuntu myself, I will help in whatever way I can if you still desire assistance. I assume you are using Ubuntu Feisty.

Though I am sure there are several different ways to do the steps listed in that post, I found it easiest to have a working Internet connection to be able to download all the packages necessary. I realize that is counter intuitive and a bit of a chicken and the egg situation. So if possible, hardwire to your router or find a wireless card that is supported out of the box. We just need to do this temporarily to get the packages. 

You can download the packages elsewhere and transfer them to your PC where Ubuntu can get at them. If that is your only option, you will need someone else to help you as I am not experienced in that area. I read somewhere that some pacakges may be available on the LiveCD if you created that. Again, no experience there. Now, on with what I do know and how I did it.....

Assuming you have hardwire capability and can connect to the internet, open a terminal. Do this instead of step 1.
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)

```
That should work and allow you to compile later on. You can disconnect you LAN connection now as you will not need it again. (as I recall and reviewed the post we both followed.)

I am using ndiswrapper 1.47. Downloaded from here: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

I also assume you have access to the .sys files mentioned. (usb8023.sys, and rndismp.sys) See the section "If you have a Windows XP installation" These are what I used.

As I recall, the instructions pretty much covered it after that point.

Although I think I may have had to do this to get IP address for the first time:
```
sudo dhclient wlan0
```
If your wireless card is not wlan0, substitute name.

Hope this helps, let me know if you get stuck, I will try to help.

---

