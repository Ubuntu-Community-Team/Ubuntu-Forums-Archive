---
title: "adding DNS?"
date: 2024-03-18
forum: Networking &amp; Wireless
---

### Post by dchmelik on 2024-03-18
Systemd/Ubuntu seemed to do another poor deviance from UNIX by making /etc/resolv.conf say don't edit without it saying what to edit.  Where do I add (with command-line text editor) more domain name servers (DNS) for when my Internet service provider's (ISP) are down? (currently were/are down)  I viewed help.ubuntu.com where search didn't show actual documentation rather than specific questions mostly 10+ years old/outdated and otherwise sometimes related but various conflicting suggestions using different configuration/software.  I'd like to add (without extra/disabling  software/daemons) about a couple dozen public/free (fallback) DNS each on their own line in a  permanent file... if simpler to put on one line, maybe comma-separated, that's fine.

---

### Post by TheFu on 2024-03-18
systemd-resolved is the tool used.  There is a config file for it.

If you don't like it, you can purge it, disable it, and do things the manual way.  I do.  For my needs, the /etc/resolv.conf has been sufficient, so purging any tool that tries to touch it is something I've done about 15 yrs.  Initially, that was resolvconf then it because systemd-resolved.  My notes say:
```
# disable resolvconf 

sudo service resolvconf status
sudo systemctl disable resolvconf.service
sudo systemctl mask resolvconf.service

sudo cp resolv.conf resolv.conf.new
sudoedit resolv.conf.new    # these lines:

# put the correct resolv.conf in place ; needs to be on 1 line
sudo mv resolv.conf resolv.conf-old ; sudo mv resolv.conf.new resolv.conf
```

**For systemd-resolved :**
The trick is to swap in the new file quickly after removing the current symlink just after you've stopped the systemd-resolved daemon.

1) create a new /etc/resolv.conf.new with the settings you want inside. Use
 ```
 sudoedit /etc/resolv.conf.new
```

2) run these commands, in order, relatively quickly:

```
  sudo systemctl stop systemd-resolved
  sudo rm /etc/resolv.conf
  sudo mv /etc/resolv.conf.new /etc/resolv.conf
  sudo chmod 644 /etc/resolv.conf
  sudo systemctl disable systemd-resolved
  sudo systemctl mask systemd-resolved
```
That's the minimal. If you like, you can purge the systemd-resolved package or not.

resolv.conf changes are immediate. No need to restart anything.

But you should do things the way you think is best.

---

### Post by dchmelik on 2024-03-18
Thanks; that's okay/good, but I read there's at least a couple ways to add more configuration and put fallback DNS in a second file?  I'd kind of like to learn that in case I work with *Ubuntu on a job in future and they want me to keep things standard.  I read one way is to install more DNS software, which I won't do, and another way is to just configure resolvconf, which I want to learn... and that now like with many things they added an entire new directory/folder somewhere in /etc just to hold maybe configuration and at least the additional file(s) of DNS servers... how would I use this setup?  I also want to learn the standard way because I'm system administrator (sysadmin) for several family PCs and would prefer they just automatically get main DNS from the router the standard way, instead of me administering /etc/resolv.conf (other than fallback) which I prefer to do on my own servers/workstations/PCs but don't want to have to on many PCs.  If no one can explain the standard way I'll eventually go ahead and use instructions above.
&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;Another issue is /usr/include/resolve.h at least used to have MAXNS=3 which I don't see anymore but apparently still is enforced another way--so how would I increase this to allow the system to be able to check up to more than 20 public/free DNS servers if the first three weren't working?

---

### Post by TheFu on 2024-03-19
> **TheFu said:**
> systemd-resolved is the tool used.  There is a config file for it.


As I said.  Thought I'd said what the file was, but it seems I got sidetracked or it was in a different thread yesterday.  There are lots of threads in these forums.
**/etc/systemd/resolved.conf ** is the file.  It is commented AND there is a manpage for the file which explains all the options.

I can only guess (I've slept since yesterday) that I thought you wanted a different solution from the time spent complaining. Guess I was wrong. Not the first time.

resolvconf is _deprecated_. Ubuntu hasn't used it in a long time - pre-16.04.  **systemd-resolved** is the tool has has been for all the currently supported Ubuntu LTS versions.  When looking for answers, always, always look at the date for the article and it is best to specify the specific Ubuntu release number.  Entire subsystems get swapped occasionally.  For example, the old "interfaces" file was removed from 18.04 for server network configuration, to be replaced by "netplan."  

Start Rant:
Netplan is YAML so much harder for humans to deal with and the capabilities of netplan aren't any more/better than the interfaces file, but it is "new" and created by Canonical, so they think it is better.  It isn't.  It is just different and it took over 2 yrs (until fall 2020), before netplan could actually support the things I needed in my network configs.  Netplan, systemd, resolved, resolvconf, wayland, snap packages are all things that I didn't want or need, but have been forced onto us in the Ubuntu server and desktop community.  We have options around most, but systemd and wayland are going to happen, regardless of the functionally that is broken along the way.  There are still, 10+ yrs later, things that systemd broke which haven't been fixed yet.
Rant End.

I cannot help with desktop networking.  The documentation for desktops is at help.ubuntu.com.  The DE will matter, but they will all have a networking tool. If DHCP is used (eeeeew, I feel dirty), then the DNS from the router should happen automagically.  Alas, when DNS breaks on Ubuntu, which seems to happen to about 1% of users, the typical fix is to add the primary and failover DNS entries to **/etc/systemd/resolved.conf **.  That can probably be done through some GUI in the desktop, but IDK. I don't use any GUI config tools myself.  I also don't use network-manager because I've been burned by it too many times.

I've never had to recompile anything on Ubuntu.  That just isn't necessary if you aren't a kernel developer.  I was an application developer for 20+ yrs before becoming an architect then enterprise architect.  Using what is built-in, assuming it works for the task, is a good idea.

So ... I can use google to find the links for desktop guides on networking.  If you are new to Ubuntu, stick with websites that have "ubuntu" in their DNS names. That's a quick filter to avoid answers that often are bad or for the wrong release or from someone excited about Linux, but now thinks they just learned of a fix/solution, because it seemed to fix their issue, when it wasn't actually their issue. Noobs get excited.

[https://help.ubuntu.com/lts/ubuntu-help/net-manual.html.en](https://help.ubuntu.com/lts/ubuntu-help/net-manual.html.en) - For the Gnome DE, these instructions specify how to manually setup the network options.

---

### Post by dchmelik on 2024-03-19
> **TheFu said:**
> [...] **/etc/systemd/resolved.conf ** is the file.  It is commented AND there is a manpage for the file which explains all the options.[...]
Thanks; I saw that, but it's poorly-commented and doesn't say there's a manpage... I know there are manpages for some files, but (some manpages are poorly-written and) not everyone knows that... viewing that, I figured out exactly how to setup fallback DNS, anyway, or perhaps will use setup you specified.
> [...] [COLOR=#000000]Netplan, systemd, resolved, resolvconf, wayland, snap packages are all things that I didn't want or need, but have been forced onto us in the Ubuntu server and desktop community.[/COLOR][...]
&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;I've never been a fan of systemd, Wayland, snap, and never used them on my own workstation personal computer (PC) except one instance systemd/GNU/Linux got display/video/graphics card computation drivers (CUDA, OpenCL) before UNIX/*BSD & non-systemd GNU/Linux, I briefly used an Ubuntu variant when I needed drivers, or when my main PC hardware malfunctioned and I used a spare family PC. Otherwise, for over 10 years I've administered Ubuntu variants for family PCs, but for reasons you describe (systemd, Wayland, snap, and now this other stuff you mentioned I mostly don't know what they are yet) and more we'll probably be switching those to non-systemd operating systems (OS).  As someone who was a college computer science (CS) major and started programming on *BSD UNIX when it was still called UNIX, I was very angry the way snap was added and makes 'mount' command practically unusable, so we removed snapd from all our PCs.  The traditional system administrator (sysadmin) (along with virtually all them) I learned from in college surely says real server OS don't have systemd.
&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;Update: I'm not a fan of the new-fangled YAML configuration file so tried to follow earlier instructions.  The following happened.
```
[FONT=monospace][COLOR=#000000]service resolvconf status[/COLOR]
systemctl disable resolvconf.service
systemctl mask resolvconf.service
Unit resolvconf.service could not be found.
Failed to disable unit: Unit file resolvconf.service does not exist.
Unit resolvconf.service does not exist, proceeding anyway.
Created symlink /etc/systemd/system/resolvconf.service &#8594; /dev/null.[/FONT]
```
&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;&#8287;I guess that was older instructions and I should've only followed the second set of instructions?

---

### Post by TheFu on 2024-03-19
systemd is part of nearly every Linux distro since around 2016, so if you are running a non-systemd distro, you are choosing to use an OS few people actually install.  That's fine, but it won't get you a job unless the company leadership is anti-systemd.  As much as I dislike systemd and think it solves issues I've never had and never wanted solved, it is the standard on all Linux systems.

mount and df!  OTOH, if you use ZFS, df has been lying to you for a while.

With Ubuntu, we need to specify versions (22.04) when we search for answers.  IF it is a GUI answer, specify the DE too.

Anyway, if this is solved, please use the _Thread Tools_ button to mark it SOLVED to help others in the community.

---

### Post by dchmelik on 2024-04-04
If you view OS family tree, even UNIX/GNU/Linux, you see systemd isn't standard (only somewhat popular); thanks for helping me avoid it... I'd rather not use it.

---

### Post by gezzer2 on 2024-04-04
not sure if this is of any help. i have systemd setup for resolving/caching DNS.

link to systemd.conf settings
[https://www.freedesktop.org/software/systemd/man/latest/resolved.conf.html](https://www.freedesktop.org/software/systemd/man/latest/resolved.conf.html)

link to setting systemd as resolving/caching.
[https://geekflare.com/linux-server-local-dns-caching/](https://geekflare.com/linux-server-local-dns-caching/)

then in settings > network connections change the DNS from auto to manual and add.
127.0.0.1 for IPV4
::1 for IPV6

as stated these maybe of help ..

my bad i didn't realise that you had solved this ..

---

### Post by TheFu on 2024-04-04
> **dchmelik said:**
> If you view OS family tree, even UNIX/GNU/Linux, you see systemd isn't standard (only somewhat popular); thanks for helping me avoid it... I'd rather not use it.

If you want to avoid systemd, Ubuntu flavors aren't for you.  Check out MX Linux, which isn't nearly as popular in the corporate world, but people who want to avoid systemd, but still sort of like Ubuntu, use it.  I think there's a debian-like distro too, that doesn't use systemd.  All the others are niche answers.  

[https://itsfoss.com/systemd-free-distros/](https://itsfoss.com/systemd-free-distros/) has a list of non-systemd distros.  Looks to me like Slackware is the biggest, but it certainly isn't as popular as it once was.  None are used much in the corporate/business world.

I ran Slackware from 1993 - 1999 when it was one of the easiest distros to use.  I hear it is about the same today, but my views on what I seek in a distro has changed over time.

---

### Post by webaake on 2024-04-04
Actually, when systemd took over DNS-resolving, it was the last straw for me. Systemd slowed down DNS-lookups quite a bit and it was really noticeable when surfing. So I uninstalled that service and went back to resolv.conf. Faster and easier to configure. This was on 18.04 and I've been running Ubuntu since like 2007 (7.04?).  I went from Ubuntu 18.04 to Devuan -no regrets.

There are a few distros without systemd like PCLinuxOS and Devuan (and more). I'm running Devuan on all my machines now and it's good! No systemd, no snapd, no flatpack - if you don't want them. They are installable.

[https://www.devuan.org/](https://www.devuan.org/)

---

