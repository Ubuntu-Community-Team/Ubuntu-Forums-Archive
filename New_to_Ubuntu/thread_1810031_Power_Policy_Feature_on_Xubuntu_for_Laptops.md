---
title: "Power Policy Feature on Xubuntu for Laptops?"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by Steff@ on 2011-07-22
Greetings everyone!

So I toyed around with different *Ubuntu shapes and forms and eventually settled for Xubuntu 11.04. to breathe some youth into my Toshiba NB205.

It basically works very well but I am missing a feature that would allow me to set the power policy so as to save battery power as much as possible when the laptop is not connected to the AC.

While experimenting with different *ubuntu versions I saw that one of the Kubuntu releases (I think it was 10.04.x) has an excellent feature that allows the user to chose between different power saving policies (e.g. "extreme power saving", "power saving", "maximum performance" etc). With that and the setting set to "extreme power saving" I managed to get over eight hours of battery life.

While Xubuntu has a basic power management feature, it does not really offer much choice and I only get between five and six hours of battery life out of it. When I switch back to Windows XP, which does have a very neat power policy feature, I get again over eight hours, so it's not the battery that's at fault.

I looked inside the synaptic package manager and the software center but could not find anything.

I also looked everywhere for some more information about this but couldn't find anything either.

Neither do I want to go back to Kubuntu as otherwise Xubuntu 11.04 works very well and is overall faster than Kubuntu.

Any hints would be most appreciated!!

---

### Post by Toz on 2011-07-22
Xubuntu has a panel plugin called "CPU Frequency Monitor" that allows you to manage the CPU governors. Right-click the panel, select Panel->Add New Items and add the CPU Frequency Monitor. If its not listed there, then you need to install it. Look for it in the Software Centre (its called xfce4-cpufreq-plugin) or open a terminal window and type in:
```
sudo apt-get install xfce4-cpufreq-plugin
```

This applet will allow you to set the CPU frequencies and governors which are similar to the ones that you saw in kubuntu and hopefully increase your battery life.

---

### Post by Steff@ on 2011-07-26
Thanks a lot Toz!

I had no problem installing the panel plugin. However, it does not seem to function properly. When I open the property settings and change the governor from the default 'on demand' setting to something else, I cannot save my choice. I only get to click 'close' but not 'save', so when I close it, the plugin still sticks with the default 'on demand' setting.

Any ideas why that could be?

---

### Post by Toz on 2011-07-26
Try disabling the ondemand service.

```
sudo update-rc.d ondemand disable
```
then reboot

---

### Post by Steff@ on 2011-07-26
Done! It now set itself to 'performance' and I still cannot change the governor in the panel plugin's preference menu.

---

### Post by Toz on 2011-07-26
Hmmm. If it's only one governor that you want (and no need for scaling to other governors), you could make a change to the ondemand init file to start that governor instead of the ondemand governor.

1. Re-enable the ondemand governor:
```
sudo update-rc.d ondemand enable
```

2. Show the available governors for your system:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

3. Edit /etc/init.d/ondemand and change the line:
> echo -n ondemand > $CPUFREQ so that you echo the appropriate governor instead of ondemand. For example, to use the conservative governor, change the line to read:
```
echo -n conservative > $CPUFREQ
```

4. Save the file and reboot. 

Hopefully it works and there's no need for the panel plugin. If however, you want to switch among governors, we'll need to do some more investigating and troubleshooting.

---

### Post by Steff@ on 2011-07-26
Basically that would be a very acceptable interim solution.

I tried that but it doesn't allow me to save the file!

---

### Post by Toz on 2011-07-26
You have to edit the file with root permissions:
```
gksudo mousepad /etc/init.d/ondemand
```

---

### Post by Steff@ on 2011-07-28
Right, I see. Well thanks a lot!! That worked!

I suppose I can always change it back to 'performance' or 'conservative' or whatever when I need to by changing the ondemand file again, right?

So in that sense this really did solve the problem.

If I knew who to talk to I would ask the developers to arrange this in a way that it would be easier to set the power settings but for now I am happy with this solution. And I guess I learned a thing or two about using the commands and all that, makes me want to learn more now.

Thanks again for your time!

---

### Post by Toz on 2011-07-28
> **Steff@ said:**
> Right, I see. Well thanks a lot!! That worked!

I suppose I can always change it back to 'performance' or 'conservative' or whatever when I need to by changing the ondemand file again, right?
Yes.
> So in that sense this really did solve the problem.

If I knew who to talk to I would ask the developers to arrange this in a way that it would be easier to set the power settings but for now I am happy with this solution. And I guess I learned a thing or two about using the commands and all that, makes me want to learn more now.

Thanks again for your time!
I believe this is a known bug but can't locate the bug report right now. I found this article the other day which seems to indicate that it is: [http://www.webupd8.org/2011/07/cpu-frequency-scaling-indicator-fixed.html]("http://www.webupd8.org/2011/07/cpu-frequency-scaling-indicator-fixed.html")

Can you please mark this thread as solved from the Thread Tools link above?

---

### Post by Steff@ on 2011-08-03
So far it's been manageable to change the ondemand file every so often. I suppose I can just wait for 11.10 to come out and hopefully it'll work then.

Thanks again!

---

