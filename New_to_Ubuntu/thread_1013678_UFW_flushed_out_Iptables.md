---
title: "UFW flushed out Iptables"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by unf4b1x on 2008-12-17
I was setting the iptables for the INPUT, OUTPUT, and FORWARD chains with just a basic configuration recently with ufw being disabled but as I enabled ufw, then checked the iptables using either ***iptables -nL*** or ***iptables -L***, everything is gone! Totally flushed out, what happened??? I thought ufw would integrate with iptables.

I got a problem saving the iptables using this: ***iptables-save > /root/ipt.save*** "Permission denied!" even though I was using sudo, so what I did was just ***iptables-save***.  I wanted it to be restored after a reboot so that I don't have to set it up again everytime I restarted. I need your thoughts, please help!

---

### Post by The Cog on 2008-12-17
ufw is a front-end for iptables. It assumes that it has full control and makes no attempt to incorporate any settings that it finds already configured there. This is true (I think) for all iptables front-ends. The solution is to use only one method to configure iptables. Do it yourself, or leave everything to your chosen front-end software.

I think you hit a problem using the pipe - the command interpreter ran iptables-save as root, but tried to write to ipt.save as you. It's probably easist to just give yourself a full root shell for a few commands - **sudo -i** will do this, and issue the commands from there:
> $ sudo -i
# iptables-save > /root/ipt.save

---

