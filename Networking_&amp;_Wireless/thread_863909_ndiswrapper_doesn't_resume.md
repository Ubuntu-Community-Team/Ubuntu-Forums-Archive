---
title: "ndiswrapper doesn't resume"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by phidia on 2008-07-19
On my hp pavilion dv6707us using 7.10 x86_64 when I resume from suspend my wireless connection doesn't. I've tried putting ndiswrapper here in the /etc/default/acpi-support file: > # Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="ndiswrapper"

But that doesn't do anything. Wireless still fails to come back after resume.
In fact nothing in that file I've tried seems to have any effect. I wonder if that acpi-support file is being used or has been replaced by something else?
There's a [bug at launchpad]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/138483") dated Sept '07 related to this but it doesn't appear to have received any attention. 
Any ideas greatly appreciated.

---

### Post by phidia on 2008-07-20
Any ideas?? Anyone have experiance with acpi-support?

---

### Post by phidia on 2008-07-25
What I've done & tried:
There are scripts available from opensuse for unloading and loading the ndiswrapper or madwifi module with suspend/resume-the trouble is they don't work consistently in opensuse either.

I found the directories in ubuntu /etc/acpi/ (sleep.d & resume.d) however placing the scripts in there doesn't accomplish anything. Those are the same directories opensuse uses for it's scripts but in opensuse the path is /etc/pm.

I had read that NM (network manager) could be the problem so I replaced NM with Wicd but that doesn't fix this either.

So basically I'm stuck with a laptop that can't resume from suspend-functionally. It does resume it's just that wireless is dead :p *Actually with Wicd suspend doesn't work right either-have to go back to NM.

Sometimes wifi resume works in opensuse but only if I'm connecting to the same network _and_ it hasn't been in suspend too long-more than 1/2 hour is too long. Macbooks with OS X are looking better all the time!

---

### Post by caljohnsmith on 2008-07-25
I've had similar issues with ndiswrapper and resuming after a suspend. What works for me is I added:
```
modprobe -r ndiswrapper
```
at the beginning of the /etc/acpi/sleep.sh script, and then at the end of the script I did:
```
modprobe ndiswrapper
ifdown wlan0
ifup wlan0
```
Then I wrote a short bash script that essentially executes "/etc/acpi/sleep.sh force" as root (with a few other extras), and that's the script that gets executed every time I hit my suspend button on my keyboard. You could give something like that a try, and if you need more details, let me know.

---

