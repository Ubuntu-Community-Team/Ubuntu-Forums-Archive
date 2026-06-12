---
title: "Setting up a proxy or VPN"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by simsimsim on 2011-06-25
Hi all,

I have found this forum very useful, so thought I'd finally register and ask a question of my own!

I have 2 computers and will shortly be moving to another country from the UK for a while. My plan is to leave one behind (set up with Ubuntu) and route my Internet traffic through it from abroad (using a Mac), so that websites think I'm in the UK.

I am a complete Linux/Ubuntu virgin, but au fait with Mac/Windows/basic networking. Hence am finding this amazingly frustrating as I cannot even work out where to start in the world of Ubuntu!

Firstly, can someone just point me in the direction of whether I want to set up a 'proxy server' (if that is even possible) on my Ubuntu machine, or whether Open VPN would be easier (that seems to be capable of doing the job from what I can gather)?

Please go easy on me; I've read threads like this one ([http://ubuntuforums.org/showthread.php?t=1777175](http://ubuntuforums.org/showthread.php?t=1777175)) and I have to say that they are beyond me, let alone the Open VPN Howto (which rather irritatingly sounds more accessible if you're using Windows!)

If someone knows of a nice GUI-based app, then that would make my day, although I fear it's going to be back to the terminal to bash a grep or something :-)

Many many thanks for any help/advice.

Simon

---

### Post by josephmills on 2011-06-25
to set up proxychains   do a ```
sudo apt-get install proxychains
``` then do a ```
sudo nano /ect/proxychains.conf
```  then just add the proxy addresses and if they are sock5 or whatever then to make your self more stealth install tor button to firefox so you are also behind that then you can add squid also be looking for hours before getting back to your og ip ;) you could also install privoxy then un-comment the the line and add the sock5 and then remove vidaila and you are even further away. but your net speed might slows down.

---

