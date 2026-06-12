---
title: "How to change default sink for Pulse Audio? To be done at command line?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by daveamay on 2011-01-03
Brand new to Ubuntu and Linux in general. I purchased a nettop from Newegg ([link]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16856107072&cm_re=jetway-_-56-107-072-_-Product")) and managed to get Ubuntu up and running, XBMC installed and the Nvidia driver updated.

Video on XBMC looks fantastic and I enjoy the Ubuntu look. However, I still don't have audio. Trying to do audio over HDMI.

I've seen several sources stating that the following must be done, 

> To get HDMI audio working:

Add: load-module module-alsa-sink device=hw:0,7 
To: /etc/pulse/default.pa

AND

run "sudo alsamixer" and unmute the 2nd SPDIF listed, (press the right arrow key to select it, then press "M" to unmute)

AND

Create /home/username/.asoundrc and populate with:

pcm.hdmi07 {
type hw
card 0
device 7
}
pcm.!default hdmi07

But there is no further description. Is this done on the command line or some other way? If so, what are the commands? I have limited experience obviously with the CL.

Thanks in advance for anyone who considers my question. I am really looking forward to using Ubuntu.

---

