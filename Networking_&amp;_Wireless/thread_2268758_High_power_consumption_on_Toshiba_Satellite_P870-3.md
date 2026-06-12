---
title: "High power consumption on Toshiba Satellite P870-303"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by ecky2 on 2015-03-11
Hi,

Problem occurs on Ubuntu installed in parallel to Windows 7 with a dual boot grub2 configuration on a Toshiba Satellite P870-303 computer.

The problem is that the laptop makes an awful noise like a vacuum cleaner just like the issue reported here : [http://ubuntuforums.org/showthread.php?t=2267614&highlight=Centrino+Wireless-N+2230](http://ubuntuforums.org/showthread.php?t=2267614&highlight=Centrino+Wireless-N+2230), with the difference that I did not do any clean-up with BleachBit. That noise came up right after installation of ubuntu 12.04 in 2013. According to powertop it was the wifi-module that produced a lot of powerconsumption. At that time I read about some WIFI problems with Toshiba Satellite computers and thought that later updates/grades would resolve the problem and tried to ignore the noise - until now.

Since this problem remains it seems evident to me that the problems  reported are not related to this one - that is confirmed by the  fact that I seem to have no connection problems (if I switch on the WIFI  - what I hardly ever do, only for testing). It's no wonder that the fan is whisteling as the part under the right  hand next to the touch-pad gets hot like a boiler plate allthough the  CPU is almost idle. So I'm astonished that even though the wifi module should be switched off (wifi deactivated) it consumes up to 30W according to powertop (although I don't know how reliable this information is, here are two excerpts I did in 1h interval (left powertop running for all that time):

```
PowerTOP 2.5      Vue d’ense Statistiques Statistiques de f Statistiques d Tunables ique                                

Re&#769;sume&#769;: 253,0 wakeups/second,  3,6 GPU ops/seconds, 0,0 VFS ops/sec and 3,2% Utilisation du processeur

Power est.              Usage       Évènements/s    Catégorie       Description
  27.8 W      0,0 pkts/s                Device         Interface réseau :  wlan0 (iwlwifi)
  3.54 W    100,0%                      Device         Périphérique radio : btusb
  907 mW      0,0 pkts/s                Device         Interface réseau :  eth0 (alx)
  487 mW    100,0%                      Device         Display backlight
  244 mW    100,0%                      Device         Display backlight
 31.1 mW    100,0%                      Device         Périphérique USB : usb-device-8087-07da
 22.9 mW      2,1 ms/s     114,0        Interrupt      [45] i915
 17.3 mW    100,0%                      Device         Codec audio hwC0D0 : Realtek
 17.3 mW    100,0%                      Device         Codec audio hwC0D3 : Intel
 4.57 mW      5,1 ms/s      25,1        Process        compiz
 3.19 mW      2,8 ms/s      15,8        Process        /usr/lib/firefox/firefox
 3.17 mW    124,3 µs/s      15,7        kWork          od_dbs_timer
 3.03 mW    572,4 µs/s      15,0        Process        syndaemon -i 1.0 -t -K -R
 2.17 mW      3,9 ms/s      11,8        Process        gnome-terminal
 1.86 mW      2,6 ms/s       9,2        Process        /usr/bin/ibus-daemon --daemonize --xim
 1.13 mW    109,2 µs/s       5,6        Process        [rcu_sched]
 995 µW       4,8 ms/s       4,9        Process        /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 875 µW      32,8 µs/s       4,3        kWork          intel_unpin_work_fn
 724 µW       0,9 ms/s       3,6        Process        /usr/lib/ibus/ibus-engine-simple
 633 µW     347,0 µs/s       3,1        Process        /usr/lib/thunderbird/thunderbird
 483 µW     199,5 µs/s       2,4        Timer          tick_sched_timer
 452 µW       8,8 µs/s       2,2        kWork          gen6_force_wake_work
 392 µW       0,9 ms/s       2,2        Process        nautilus -n
 392 µW     335,2 µs/s       1,9        Timer          hrtimer_wakeup
 282 µW     116,1 µs/s       1,4        Process        /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
 271 µW      51,5 µs/s       1,3        Interrupt      [4] block(softirq)
 251 µW       1,2 ms/s       1,2        Process        /usr/lib/unity/unity-panel-service
 181 µW      90,0 µs/s       0,9        Process        acpid -c /etc/acpi/events -s /var/run/acpid.socket
 181 µW      33,8 µs/s       0,9        Interrupt      [47] nouveau
 181 µW       3,2 µs/s       0,9        kWork          console_callback
 171 µW      14,2 µs/s       0,8        kWork          flush_to_ldisc
 161 µW     314,3 µs/s       0,8        Process        /usr/lib/ibus/ibus-ui-gtk3
 121 µW     448,4 µs/s       0,6        Process        bash
 101 µW     201,4 µs/s       0,5        Process        /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
 101 µW       8,3 µs/s       0,5        kWork          i915_gem_retire_work_handler
 101 µW       0,0 µs/s       0,5        kWork          disk_events_workfn
    0 mW     77,8 µs/s       0,4        Process        upstart-dbus-bridge --daemon --session --user --bus-name session
    0 mW     26,0 µs/s       0,4        Timer          watchdog_timer_fn
    0 mW      2,6 µs/s       0,3        kWork          i915_gem_idle_work_handler
    0 mW    122,3 µs/s      0,30        Process        /usr/lib/upower/upowerd
    0 mW    119,6 µs/s      0,30        Process        /usr/lib/unity-settings-daemon/unity-settings-daemon
    0 mW     22,4 µs/s      0,30        Process        /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service



PowerTOP 2.5      Vue d’ense Statistiques Statistiques de f Statistiques d Tunables ique                                

Re&#769;sume&#769;: 763,6 wakeups/second,  29,5 GPU ops/seconds, 0,0 VFS ops/sec and 32,2% Utilisation du processeur

Power est.              Usage       Évènements/s    Catégorie       Description
  15.3 W      0,0 pkts/s                Device         Interface réseau :  wlan0 (iwlwifi)
  6.79 W      0,0 pkts/s                Device         Interface réseau :  eth0 (alx)
  5.82 W    100,0%                      Device         Périphérique radio : btusb
  1.14 W    100,0%                      Device         Codec audio hwC0D3 : Intel
  1.14 W    100,0%                      Device         Codec audio hwC0D0 : Realtek
  481 mW    100,0%                      Device         Display backlight
  343 mW    217,9 ms/s     341,1        Process        /usr/lib/firefox/firefox
  240 mW    100,0%                      Device         Display backlight
 66.5 mW     21,2 ms/s      86,8        Process        compiz
 14.2 mW     38,1 ms/s      30,3        Process        gnome-system-monitor
 8.11 mW    394,1 µs/s       8,9        Process        syndaemon -i 1.0 -t -K -R
 501 µW       1,1 ms/s       6,0        Process        /usr/lib/thunderbird/thunderbird
 501 µW     439,3 µs/s       0,6        Process        gnome-terminal
 100 µW      41,1 µs/s      0,20        Process        /usr/lib/unity-settings-daemon/unity-settings-daemon
 100 µW      18,8 µs/s      0,25        Process        /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
    0 mW     22,0 ms/s      16,2        Process        /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
    0 mW      4,8 ms/s      22,9        Process        /usr/bin/ibus-daemon --daemonize --xim
    0 mW      2,7 ms/s      75,9        Interrupt      [45] i915
    0 mW      1,6 ms/s      34,2        Timer          hrtimer_wakeup
    0 mW      1,5 ms/s       7,0        Process        /usr/lib/ibus/ibus-engine-simple
    0 mW      1,0 ms/s      10,0        Timer          tick_sched_timer
    0 mW      0,8 ms/s      0,00        Timer          delayed_work_timer_fn
    0 mW      0,8 ms/s      0,05        Process        powertop
    0 mW      0,8 ms/s       0,7        Process        /usr/lib/unity/unity-panel-service
    0 mW    694,3 µs/s      64,5        kWork          od_dbs_timer
    0 mW    681,5 µs/s      0,00        Process        [kworker/u16:1]
    0 mW    588,3 µs/s       8,2        Process        scite
    0 mW    540,1 µs/s       3,1        Process        /usr/lib/ibus/ibus-ui-gtk3
    0 mW    456,1 µs/s       6,2        Process        scite Forums.txt
    0 mW    404,5 µs/s      0,00        Interrupt      [1] timer(softirq)
    0 mW    276,2 µs/s      0,20        Interrupt      [7] sched(softirq)
    0 mW    216,7 µs/s      0,30        Interrupt      [41] xhci_hcd
    0 mW    192,6 µs/s      29,3        kWork          intel_unpin_work_fn
    0 mW    190,2 µs/s       1,2        Process        /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
    0 mW    163,7 µs/s      11,0        Process        [rcu_sched]
    0 mW    162,8 µs/s      0,05        Process        [rcuos/2]
    0 mW    141,2 µs/s       1,8        Process        acpid -c /etc/acpi/events -s /var/run/acpid.socket
    0 mW    132,2 µs/s       0,5        Interrupt      [3] net_rx(softirq)
    0 mW    125,0 µs/s      0,00        Process        [kworker/5:1]
    0 mW    119,5 µs/s      0,30        Process        /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
    0 mW    117,0 µs/s      0,00        Process        [kworker/0:0]
    0 mW    109,0 µs/s      0,20        Interrupt      [48] eth0

```

So now, do you have any idea what is going wrong ? I put the results of the wireless script to an attachement for more information. Where should I look into to investigate further? 
- Change some configuration? as the problem reported by docdoc2 may imply that some necessary configuration files had been erased this may be an option ... but where are they and what files to search for and what to change in them if found?
- Compile a personnalized Kernel - but with what options/parameters ?

I would very much appreciate some pointers.

Thanks in advance
ecky

PS: Forgot to mention that there is no noise when the laptop is running  under Windows and powerconsumtion is low : On battery I was able to work  2h instead of a couple of minutes with Ubuntu.

PPS: hadent my glasses on when I first read the model-number it is not P670-303 but P870-303

---

### Post by ecky2 on 2015-03-17
Hello,

Things are getting worse: I just started with a BIOS-update to see if that would change anything - it didn't concerning the power-consumption problem, but concerning start up: yesterday right after the update the computer had problems to get up and running. Today, after a night of cooling down, it does not even get to the BIOS! When I press the power button the power diode lightens up, the WIFI diode lights up and fan and hdd spin up. Then all stops and starts over a few seconds later. No possibility to get to the BIOS or whatsoever - probably the startup process is interrupted before the machine even gets to read the keyboard ... I think all that might help is a screw-driver :-( don't know if I will get that fixed ...

ecky

---

### Post by kerry_s on 2015-03-17
install intel-microcode

sudo apt-get install intel-microcode

---

### Post by ecky2 on 2015-03-17
thanx, I'll try that as soon as I get it booting.

---

### Post by ecky2 on 2015-04-30
Finally the motherboard is dead. When opening the case of the laptop I found out that around a non-cooled big IC the MB got teinted a bit brown/yellow at exactly the place where the computer got hot all the time.

So what went on? I'm not shure, as I'm not an electronics expert, but the chip in question seems to be the Intel south or north bridge that also contains graphics functionnality. With Linux, I was not using the on board Nvidia chip, as I could not get it to work properly and Intel was installed by default and working fine, so I just left it that way. I think that that chip just burned as it was not cooled and did the work for the Nvidia graphic chip which in turn was cooled but idle.

Possible consequences:
I've been using Linux for a long time and I know the risks and I'm not going to declare anyone responsible for this but myself, and all Linux developpers do a tremendous job for free that I profit from. However, looking at the experience, I'd like to engage the following consideration:
It might be dangerous, at least on some laptop/portable computers that may not cool all chips (most probably because of cost effectiveness or space restrictoins), to install Intel drivers by default. It might be a good thing to integrate a warning into the installation process.

 And a tip for all laptop and portable users that would like to use Linux on them: If the machine gets hot, you NEED to reconfigure your system (even though it seems to work fine otherwise) so that it does not get hot. It seems not dangerous to test though, as it took more than a year to grill the chip in my case.

So long
ecky

PS: I close this thread now. However, if you are a developer and have further questions, feel free to contact me

---

