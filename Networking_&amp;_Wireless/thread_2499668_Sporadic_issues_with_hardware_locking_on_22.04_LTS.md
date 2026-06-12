---
title: "Sporadic issues with hardware locking on 22.04 LTS"
date: 2024-08-06
forum: Networking &amp; Wireless
---

### Post by verdalexion on 2024-08-06
I have come across an issue that no amount of googling seems to be able to solve. I have some tablet style devices that we have now dual booted with windows IoT and ubuntu Desktop. Strangely when we build and after 3 or so restarts ubuntu will go into wireless hardware lock. There is no physical hardware lock button on these devices, keyboard shortcuts do not seem to work either. the only way around this has been to log into the windows partition connect to a wireless source and then reboot back into the ubuntu install. This will then work for a few restarts then the cycle repeats. the only working Soloution I have come across is to cover pin 20 on the nic however as these are IP rated any disassembly is not an option. Any ideas on a work around or the root cause of the isue would be appreciated

---

### Post by slovenskekasina on 2024-08-06
Try disabling Fast Startup to see if it resolves the issue.
**Steps to Disable Fast Startup**:

[LIST=1]
[*]Open Control Panel.
[*]Go to Power Options.
[*]Click on "Choose what the power buttons do".
[*]Click on "Change settings that are currently unavailable".
[*]Uncheck "Turn on fast startup (recommended)".
[*]Save changes and reboot.
[/LIST]

---

### Post by TheFu on 2024-08-06
1. Check the system logs for warnings, errors and issues. (Use google with each line, removing those parts of the error that are specific to your instance, like timestamps, but keep the parts with the error and hardware specifics except serial numbers)
2. Look at the detailed hardware report, which drivers are used, and any known issues for that specific hardware and drivers (use google with the hardware chips)
3. Fix each known issue.
4. Repeat.

If you expect people here to help, you'll need to have done those things.
Odd brand hardware are usually really great at using standard components which are well supported by Linux or they use off-brand cheap quality components that other brands won't touch.  Once in a while a famous brand will do this with a few new, cheap, chips, and make linux support a challenge.  Lenovo did this a few times on their very cheap laptops. Took 2 years before the kernel support for some of those chips became normal.  Imagine buying a Lenovo laptop and not being able to use the wifi for 2 yrs.  After 1 yr, there were wifi drivers available, which needed to be manually installed using about 20 steps.

If you are in a real hurry and want the system to be supported sooner, ship the device to a kernel developer and discuss paying them.

Of course, it could just be bad hardware that is broken and should be returned for replacement.  The system logs should help determine that.  If you don't know how to find and read system logs, use google. There are lots of guides.  

Lastly, if the hardware is really, really, new, the kernel from April may not have solid support for it.  Look to using the latest kernels and hope those have support for the bleeding edge hardware.

---

