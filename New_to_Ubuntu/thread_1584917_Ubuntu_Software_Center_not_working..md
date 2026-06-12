---
title: "Ubuntu Software Center not working."
date: 2010-09-29
forum: New to Ubuntu
---

### Post by GiuHei3u on 2010-09-29
Diving in and getting my feet wet and after reading one of the tutorials about using the Software Center I wanted to try my hand at downloading an alarm clock. I clicked on Accessories and clicked on the Alarm Clock. Then clicked on Install. Nothing. No window asking me for my password. I tried multiple times and nada. 

What is going on?

Thanks.

---

### Post by Dustin2128 on 2010-09-29
what do you mean? did you install it with the software center first? 
the software center shouldn't be under a menu anymore (with lucid), it's just an item of its own under applications.

---

### Post by Darkness Des on 2010-09-29
Some more details would be nice. Such as:

Are you running as the "root" or admin user?
Do you know the name of the Alarm clock you are trying to download?
What are the exact steps that you are doing?

---

### Post by dFlyer on 2010-09-29
Not sure what is going on. I just tried it here and everything works great. Have you tried synaptic under system/administration. You might want to try to reinstall software center to see that will fix any problem.

---

### Post by GiuHei3u on 2010-09-29
> **Darkness Des said:**
> Some more details would be nice. Such as:

Are you running as the "root" or admin user?
Do you know the name of the Alarm clock you are trying to download?
What are the exact steps that you are doing?

Sure, thanks.
Top left I clicked on Applications/Ubuntu Software Center/Accessories/Alarm Clock.
Clicked on the Install button and nothing. Running Ubuntu 10.04

Hmmm. Not sure if I am running as Root or Admin. How can I determine that. I am the 
only user of this computer and installed the program.

---

### Post by sisco311 on 2010-09-29
Is policykit running? What's the output of:
```
ps -ef | grep polkit
```
?

Does the authentication agent work? What happens if you run:
```
pkexec echo
```
?

---

### Post by GiuHei3u on 2010-09-29
> **sisco311 said:**
> Is policykit running? What's the output of:
```
ps -ef | polkit
```?

Does the authentication agent work? What happens if you run:
```
pkexec echo
```?

polkit,,,,,command not found


pkexec echo....
Error executing command as another user: No authentication agent was found.

---

### Post by sisco311 on 2010-09-29
> **gumshoegrant said:**
> polkit,,,,,command not found


Oh, sorry, it's:
```
ps -ef | grep polkit
```

But, anyway... 
> **gumshoegrant said:**
> 
pkexec echo....
Error executing command as another user: No authentication agent was found.

Log out and log back in and see if that solves the issue.

If not, then try to start the authentication agent:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```
and check out if Software Center works.

If yes, then add the authentication agent to the startup applications:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
sed -i 's/NoDisplay=true/NoDisplay=false/' ~/.config/autostart/polkit-gnome-authentication-agent-1.desktop
```

---

### Post by Dustin2128 on 2010-09-29
> **gumshoegrant said:**
> Sure, thanks.
Top left I clicked on Applications/Ubuntu Software Center/Accessories/Alarm Clock.
Clicked on the Install button and nothing. Running Ubuntu 10.04

Hmmm. Not sure if I am running as Root or Admin. How can I determine that. I am the 
only user of this computer and installed the program.
you're most likely not; I'm thinking ubuntu disables this by default. Try installing via synaptic package manager, or see if this works:
```
sudo apt-get install alarm-clock alarm-clock-applet

```

---

### Post by GiuHei3u on 2010-09-29
> **sisco311 said:**
> Oh, sorry, it's:
```
ps -ef | grep polkit
```But, anyway... 


Log out and log back in and see if that solves the issue.

If not, then try to start the authentication agent:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```and check out if Software Center works.

If yes, then add the authentication agent to the startup applications:
```
mkdir -p ~/.config/autostart/
cp /etc/xdg/autostart/polkit-gnome-authentication-agent-1.desktop ~/.config/autostart/
sed -i 's/NoDisplay=true/NoDisplay=false/' ~/.config/autostart/polkit-gnome-authentication-agent-1.desktop
```

Sisco thanks!
I did both commands but did not do the authenitication agent to the startup apps but here is the result of the two commands....

(polkit-gnome-authentication-agent-1:1677): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1677): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

---

### Post by sisco311 on 2010-09-29
Looks like this BUG:
[https://bugs.launchpad.net/debian/+source/policykit-1-gnome/+bug/449378](https://bugs.launchpad.net/debian/+source/policykit-1-gnome/+bug/449378)

Try to update your system:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by GiuHei3u on 2010-09-29
> **sisco311 said:**
> Looks like this BUG:
[https://bugs.launchpad.net/debian/+source/policykit-1-gnome/+bug/449378](https://bugs.launchpad.net/debian/+source/policykit-1-gnome/+bug/449378)

Try to update your system:
```
sudo apt-get update
sudo apt-get upgrade
```

Thanks Sisco. Going to give it a rest for the evening and try it tomorrow. Will get back with you. 
Good Night.

---

### Post by Dustin2128 on 2010-09-29
> **gumshoegrant said:**
> Thanks Sisco. Going to give it a rest for the evening and try it tomorrow. Will get back with you. 
Good Night.
updates usually take a while, at least get them started!

---

