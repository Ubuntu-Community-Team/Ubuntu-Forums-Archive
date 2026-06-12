---
title: "I'd like to know how to completely remove PIA VPN please."
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by jimijives on 2018-02-17
Hi, when I installed Private Internet Access I just copy and pasted the simple commands on their web site.  (tar -xzf pia-v75-installer-linux.tar.gz  -  ./pia-v75-installer-linux.sh)  However I have searched Google and I can't seem to find the commands to totally remove it before I install it again.  The reason is last night it was working no problem for 4 hours and I haven't changed any settings but today it won't connect at all so I'm hoping a reinstall will help.  Thank you for any advice.  I typed seperated lines in this post to make it easier to read, I don't know why it's formatting it all together making it look a bit messy sorry.

---

### Post by TheFu on 2018-02-17
PIA works with a stock openvpn installation. Only the config files are needed.  This is how I use PIA (and my own VPN running from home).

So ... you should probably look at  ./pia-v75-installer-linux.sh to see what it does.  Might want to ask this same question with the PIA support guys.

I've never installed PIA using their stuff ... just copied their config files (be certain to get the AES256 stuff) and pick which exit location I need.

---

### Post by jimijives on 2018-02-17
Hi TheFu, thanks for the advice.  I shall try and do some research to see how I can achieve this.  I'm quite sure PIA installs OpenVPN at the same time as it's own software as it relies on it.

---

### Post by TheFu on 2018-02-17
> **jimijives said:**
> Hi TheFu, thanks for the advice.  I shall try and do some research to see how I can achieve this.  I'm quite sure PIA installs OpenVPN at the same time as it's own software as it relies on it.

Does it use the package manager version or some old, crufty, version that hasn't been patched constantly?

---

### Post by litlesam on 2018-02-17
Hi, [This]("https://helpdesk.privateinternetaccess.com/hc/en-us/articles/232054147-How-can-I-uninstall-reinstall-your-application-on-Linux-") is from the pia site.

---

### Post by vincentertainment on 2018-02-25
I'm due to uninstall and try re-installing myself. I may just go back to using it with OpenVPN settings.

```
rm -rf ~/.pia_manager/
rm ~/.local/share/applications/pia_manager.desktop

```

[https://helpdesk.privateinternetaccess.com/hc/en-us/articles/232054147-How-can-I-uninstall-reinstall-your-application-on-Linux-](https://helpdesk.privateinternetaccess.com/hc/en-us/articles/232054147-How-can-I-uninstall-reinstall-your-application-on-Linux-)

Private Internet Access with OpenVPN instructions here:
[https://www.youtube.com/watch?v=s8F2oPWpTGM&index=6&list=PLAcLkzR0TiBku2dUNStulZjUJgNZ_6NRH](https://www.youtube.com/watch?v=s8F2oPWpTGM&index=6&list=PLAcLkzR0TiBku2dUNStulZjUJgNZ_6NRH)

Hope that helps

---

