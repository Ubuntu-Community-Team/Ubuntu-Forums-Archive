---
title: "Battery Problem"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by hillbillyhotrod on 2011-02-26
So I bought used a laptop (HP Compaq nc640) just so I could learn and play with Ubuntu, I love it.  When I bought it He told me the battery was shot, plugged in it worked fine so I bought it. I went and bought a new battery and it charges up says its charged but when unplugged it says it going to go into hibernation mood if not plugged in. Think its a bad battery, bad internal charging problem or something else? I'm lost with these types of things.

---

### Post by acrazyplayer on 2011-02-26
I suppose it could be a few things.

1. Another shot batter (probably)
2. Laptop no longer charges your battery's (doubt it)
3. Ubuntu is failing to recognize the correct level of charge and always wants to hibernate (maybe)

I suggest looking into the 3rd scenario as that would be the cheapest option and see what you can find out.

---

### Post by hillbillyhotrod on 2011-02-26
How would I go about doing that?

---

### Post by acrazyplayer on 2011-02-27
I have went looking for bugs regarding wrong percentage readings and did find a few, the same thing most of them said was that the gnome-power-manager was at fault, so there were a few options but I think the easiest one was to try out kubuntu and see how that handles your battery because they use their own power manager.

If you really dont want to try kubuntu (btw just run "sudo tasksel" in a terminal and choose "kbuntu desktop" by pushing the space button on it) because of the big download size then you could try upgrading gnome-power-manager to the very newest and see how that helps.

---

### Post by rvchari on 2011-02-27
> **acrazyplayer said:**
> I have went looking for bugs regarding wrong percentage readings and did find a few, the same thing most of them said was that the gnome-power-manager was at fault, so there were a few options but I think the easiest one was to try out kubuntu and see how that handles your battery because they use their own power manager.

If you really dont want to try kubuntu (btw just run "sudo tasksel" in a terminal and choose "kbuntu desktop" by pushing the space button on it) because of the big download size then you could try upgrading gnome-power-manager to the very newest and see how that helps.
xfce desktop is another option that is light wt and can be checked as you had said !

---

### Post by fabricator4 on 2011-02-27
> **hillbillyhotrod said:**
> So I bought used a laptop (HP Compaq nc640) just so I could learn and play with Ubuntu, I love it.  When I bought it He told me the battery was shot, plugged in it worked fine so I bought it. I went and bought a new battery and it charges up says its charged but when unplugged it says it going to go into hibernation mood if not plugged in. Think its a bad battery, bad internal charging problem or something else? I'm lost with these types of things.

ACPI is broken in the BIOS of some older computers (ie it doesn't work the way Linux expects it to).

See if there's a selection in the BIOS of the computer to turn ACPI off.

Chris

---

### Post by hillbillyhotrod on 2011-02-27
How do I find a upgraded power manager or BIOS section, how safe would it be to run "sudo taskel" and choose kubuntu? What would happen?

---

### Post by hillbillyhotrod on 2011-02-27
Here is the latest. while plugged in it said it only had 3.3% and aprox 3 min. left. I unplugged it and am posting with it now a 0% charge with no problems. I am totally mystified with what is going on

---

### Post by hillbillyhotrod on 2011-02-27
ok so, I went for a while but stayed on 0% and I couldn't take not knowing what was going on so I had a **** with Linux mint 10, open suse 11.4 milestone and fedora 14 so i decided to give Linux mint a try and see what its like seeing as how I'm still new to Linux. I'm sure I will be back to Ubuntu after a little while.

---

### Post by acrazyplayer on 2011-02-28
running tasksel would just install the kubuntu desktop with all of kubuntus applications and packages, so it would be like having two different operating systems almost.

If you feel up for it try pclinuxos, that's my favourite besides ubuntu and it detects hardware a little different, Linux mint is based off of ubuntu so you could still have the same problem with that.

---

### Post by hillbillyhotrod on 2011-02-28
Thanks I'm gonna give this a try for a little while then I will probably give that a try, Its to bad I really like Ubuntu. It's probably gonna have to wait till I get a different computer

---

### Post by hillbillyhotrod on 2011-03-06
So I popped in a xubuntu disk and noticed that was telling me that the battery was empty and it was running on AC power so I'm going to have to guess that the brand new battery is a dud.

---

