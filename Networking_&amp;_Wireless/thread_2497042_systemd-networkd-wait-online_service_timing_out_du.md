---
title: "systemd-networkd-wait-online service timing out during boot 22.04.4 LTS"
date: 2024-04-21
forum: Networking &amp; Wireless
---

### Post by JayCroghan on 2024-04-21
I have this issue with [COLOR=#0C0D0E][FONT=ui-monospace]systemd-networkd-wait-online.service[/FONT][/COLOR] timing out during boot but the fix hasn't been a single one of the myriad of fixes I have found online.

Let me start at the start:

I have been this issue for quite a while so today I have tried a suggestion I found online and running [COLOR=#0C0D0E][FONT=ui-monospace]systemd-analyze plot[/FONT][/COLOR] and checking the output.


I'm attaching the SVG file here because unless I am mistaken there are only two things taking an absurdly long time to boot, one of them [COLOR=#0C0D0E][FONT=ui-monospace]systemd-networkd-wait-online[/FONT][/COLOR] (of course) but then afterwards, strangely, [COLOR=#0C0D0E][FONT=ui-monospace]sendmail[/FONT][/COLOR] which I do not even use on this server it is within my home network and only functions as a seedbox/media server.


Am I missing something here? I disabled [COLOR=#0C0D0E][FONT=ui-monospace]wlan[/FONT][/COLOR] previously to rule it out as it's a wired  machine and has no need for [COLOR=#0C0D0E][FONT=ui-monospace]wlan[/FONT][/COLOR]. 


[https://c0ld.net/slowboot.svg](https://c0ld.net/slowboot.svg)


I disabled [COLOR=#0C0D0E][FONT=ui-monospace]sendmail[/FONT][/COLOR], rebooted, watched it timeout and then ran it again and now the only thing taking time is the thing I'm trying to fix.


[https://c0ld.net/slowboot-nosendmail.svg](https://c0ld.net/slowboot-nosendmail.svg)


Here is a full journalctl: [http://0x0.st/Xo36.txt](http://0x0.st/Xo36.txt)


It has a static IP, it is not internet facing, runs [COLOR=#0C0D0E][FONT=ui-monospace]plex[/FONT][/COLOR], [COLOR=#0C0D0E][FONT=ui-monospace]bittorrent-nox[/FONT][/COLOR], [COLOR=#0C0D0E][FONT=ui-monospace]jellyfin[/FONT][/COLOR] and has a couple of USB hard drives mounted at boot for storage and that's about all that's running other than [COLOR=#0C0D0E][FONT=ui-monospace]webmin[/FONT][/COLOR] and [COLOR=#0C0D0E][FONT=ui-monospace]cockpit[/FONT][/COLOR]. It has the full Ubuntu GNome installed but not booting at startup, I just wanted it for kicks and giggles in case if I need to ever use it as a backup PC.


I really do not want to simply mask the problem by disabling the service. I even tried changing to [COLOR=#0C0D0E][FONT=ui-monospace]renderer: networkd[/FONT][/COLOR] from [COLOR=#0C0D0E][FONT=ui-monospace]renderer: NetworkManager[/FONT][/COLOR] in [COLOR=#0C0D0E][FONT=ui-monospace]netplan[/FONT][/COLOR]


Output of [COLOR=#0C0D0E][FONT=ui-monospace]networkctl[/FONT][/COLOR], [COLOR=#0C0D0E][FONT=ui-monospace]wlan[/FONT][/COLOR] is not configured on purpose.


[COLOR=#0C0D0E][FONT=ui-monospace]IDX LINK   TYPE     OPERATIONAL SETUP
  1 lo     loopback carrier     unmanaged
  2 eno1   ether    routable    configured
  3 wlp1s0 wlan     off         unmanaged


3 links listed.
[/FONT][/COLOR]

So nothing crazy there.


I also have [COLOR=#0C0D0E][FONT=ui-monospace]optional: true[/FONT][/COLOR] under config of eno1 in netplan, changing it to false makes no difference.


I also tried adding [COLOR=#0C0D0E][FONT=ui-monospace]--any[/FONT][/COLOR] and then [COLOR=#0C0D0E][FONT=ui-monospace]--interface=eno1[/FONT][/COLOR] as specified below (restarting the service both times) and both still have the same timeout.
[https://ubuntuforums.org/showthread.php?t=2490962](https://ubuntuforums.org/showthread.php?t=2490962)


```
Apr 21 15:15:16 jays-lenovo systemd[1]: Starting Wait for Network to be Configured...
&#9617;&#9617; Subject: A start job for unit systemd-networkd-wait-online.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd-wait-online.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 3886.
Apr 21 15:17:16 jays-lenovo systemd-networkd-wait-online[4967]: Timeout occurred while waiting for network connectivity.
Apr 21 15:17:16 jays-lenovo systemd[1]: systemd-networkd-wait-online.service: Main process exited, code=exited, status=1/FAILURE
&#9617;&#9617; Subject: Unit process exited
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; An ExecStart= process belonging to unit systemd-networkd-wait-online.service has exited.
&#9617;&#9617;
&#9617;&#9617; The process' exit code is 'exited' and its exit status is 1.
Apr 21 15:17:16 jays-lenovo systemd[1]: systemd-networkd-wait-online.service: Failed with result 'exit-code'.
&#9617;&#9617; Subject: Unit failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; The unit systemd-networkd-wait-online.service has entered the 'failed' state with result 'exit-code'.
Apr 21 15:17:16 jays-lenovo systemd[1]: Failed to start Wait for Network to be Configured.
&#9617;&#9617; Subject: A start job for unit systemd-networkd-wait-online.service has failed
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd-wait-online.service has finished with a failure.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 3886 and the job result is failed.

```

This was after restarting the service with [COLOR=#0C0D0E][FONT=ui-monospace]--interface=eno1[/FONT][/COLOR] which is most definitely up!!!!


The same check for [COLOR=#0C0D0E][FONT=ui-monospace]systemd-networkd.service[/FONT][/COLOR]


```

-- Boot 984031206640442cb02a40798ddf3b7f --
Apr 21 14:21:12 jays-lenovo systemd[1]: Starting Network Configuration...
&#9617;&#9617; Subject: A start job for unit systemd-networkd.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 49.
Apr 21 14:21:12 jays-lenovo systemd-networkd[1178]: lo: Link UP
Apr 21 14:21:12 jays-lenovo systemd-networkd[1178]: lo: Gained carrier
Apr 21 14:21:12 jays-lenovo systemd-networkd[1178]: Enumeration completed
Apr 21 14:21:12 jays-lenovo systemd[1]: Started Network Configuration.
&#9617;&#9617; Subject: A start job for unit systemd-networkd.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd.service has finished successfully.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 49.
Apr 21 14:23:15 jays-lenovo systemd-networkd[1178]: eno1: Link UP
Apr 21 14:23:18 jays-lenovo systemd-networkd[1178]: eno1: Gained carrier
Apr 21 14:23:19 jays-lenovo systemd-networkd[1178]: eno1: Gained IPv6LL
Apr 21 14:51:50 jays-lenovo systemd-networkd[1178]: eno1: Re-configuring with /run/systemd/network/10-netplan-eno1.network
Apr 21 14:51:51 jays-lenovo systemd-networkd[1178]: eno1: Re-configuring with /run/systemd/network/10-netplan-eno1.network
Apr 21 14:51:51 jays-lenovo systemd-networkd[1178]: eno1: DHCPv6 lease lost
Apr 21 14:52:23 jays-lenovo systemd[1]: Stopping Network Configuration...
&#9617;&#9617; Subject: A stop job for unit systemd-networkd.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A stop job for unit systemd-networkd.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 4966.
Apr 21 14:52:23 jays-lenovo systemd-networkd[1178]: eno1: DHCPv6 lease lost
Apr 21 14:52:23 jays-lenovo systemd[1]: systemd-networkd.service: Deactivated successfully.
&#9617;&#9617; Subject: Unit succeeded
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; The unit systemd-networkd.service has successfully entered the 'dead' state.
Apr 21 14:52:23 jays-lenovo systemd[1]: Stopped Network Configuration.
&#9617;&#9617; Subject: A stop job for unit systemd-networkd.service has finished
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A stop job for unit systemd-networkd.service has finished.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 4966 and the job result is done.
-- Boot dc2cb94cb1f649c49648ba8e085192db --
Apr 21 14:53:19 jays-lenovo systemd[1]: Starting Network Configuration...
&#9617;&#9617; Subject: A start job for unit systemd-networkd.service has begun execution
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd.service has begun execution.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 25.
Apr 21 14:53:19 jays-lenovo systemd-networkd[1172]: lo: Link UP
Apr 21 14:53:19 jays-lenovo systemd-networkd[1172]: lo: Gained carrier
Apr 21 14:53:19 jays-lenovo systemd-networkd[1172]: Enumeration completed
Apr 21 14:53:19 jays-lenovo systemd[1]: Started Network Configuration.
&#9617;&#9617; Subject: A start job for unit systemd-networkd.service has finished successfully
&#9617;&#9617; Defined-By: systemd
&#9617;&#9617; Support: http://www.ubuntu.com/support
&#9617;&#9617;
&#9617;&#9617; A start job for unit systemd-networkd.service has finished successfully.
&#9617;&#9617;
&#9617;&#9617; The job identifier is 25.
Apr 21 14:53:19 jays-lenovo systemd-networkd[1172]: eno1: Link UP
Apr 21 14:53:22 jays-lenovo systemd-networkd[1172]: eno1: Gained carrier
Apr 21 14:53:24 jays-lenovo systemd-networkd[1172]: eno1: Gained IPv6LL
Apr 21 15:26:32 jays-lenovo systemd-networkd[1172]: eno1: Re-configuring with /run/systemd/network/10-netplan-eno1.network
Apr 21 15:26:32 jays-lenovo systemd-networkd[1172]: eno1: DHCPv6 lease lost
Apr 21 15:26:32 jays-lenovo systemd-networkd[1172]: eno1: Re-configuring with /run/systemd/network/10-netplan-eno1.network
Apr 21 15:26:32 jays-lenovo systemd-networkd[1172]: eno1: DHCPv6 lease lost

```

Full [https://c0ld.net/dmesg.html]("http://sc0ld.net/dmesg.html") available here. I do not know what else to try at this point, I have scoured the internet.

eno1 is configured as a static IP too so it makes no sense it's taking *[I]longer*[/I] to be available than shorter.
[192.168.2.1]("http://192.168.2.1") is the main router for my entire household with multiple different routers and tens of devices, not a single other one has any issue.
```

# This is the network config written by 'subiquity'
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      optional: false
      addresses:
        - 192.168.2.99/24
      nameservers:
        addresses: [192.168.2.1]
      routes:
        - to: default
          via: 192.168.2.1

```

---

### Post by VMC on 2024-04-21
Read this [link]("https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456") on [COLOR=#0C0D0E][FONT=ui-monospace]systemd-networkd-wait-online.service and apply suggested fix.[/FONT][/COLOR]

---

### Post by JayCroghan on 2024-04-21
Are you referring specifically to removing the couple of seconds by disabling those ccouple of unnecesary services? Considering the timeout is in minutes and this server isn't really doing much, even though I knew this was going to do nothing I went ahead anyway. Similar to the person in that thread, this is after removing those services:

systemd-analyze critical-chain
```

The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.


multi-user.target @2min 19.505s
&#9492;&#9472;snapd.seeded.service @2min 6.485s +12.979s
  &#9492;&#9472;basic.target @2min 6.389s
    &#9492;&#9472;sockets.target @2min 6.384s
      &#9492;&#9472;cockpit.socket @2min 6.324s +56ms
        &#9492;&#9472;sysinit.target @2min 6.213s
          &#9492;&#9472;cloud-init.service @2min 5.715s +491ms
            &#9492;&#9472;cloud-init-local.service @4.148s +1.183s
              &#9492;&#9472;systemd-remount-fs.service @1.200s +106ms
                &#9492;&#9472;systemd-journald.socket @1.015s
                  &#9492;&#9472;system.slice @967ms
                    &#9492;&#9472;-.slice @967ms

```

All of them are ion seconds, but beging @2 min+. The services are not the issue. My home network isn't the issue. Something is causing my eth0 (which for some reason is renamed eno1 and not by me) to take 2+ mins to get a link on a hard wired 1 Gb wired connection. I can internet test around 850Mbs so it's not just link speed.

I read the whole rest of that thread in case I am missing something silly, and I'm not sure I am? I summed up the entire list of systemd-analyze blame which is 106 seconds plus 2000ms~ so 108 seconds. That is still leaving something like 1 minute 40 seconds of time unaccounted for?

Here is the full blame anyway:
```

2min 100ms systemd-networkd-wait-online.service
   11.436s snapd.seeded.service
   11.294s snapd.service
   10.711s snap.lxd.activate.service
    5.624s webmin.service
    4.886s postgresql@14-main.service
    3.553s containerd.service
    2.569s dev-mapper-ubuntu\x2d\x2dvg\x2dubuntu\x2d\x2dlv.device
    2.165s nmbd.service
    2.000s pmlogger.service
    1.889s dev-loop14.device
    1.888s dev-loop12.device
    1.886s dev-loop8.device
    1.871s qbittorrent-nox.service
    1.863s dev-loop11.device
    1.851s dev-loop17.device
    1.851s dev-loop15.device
    1.827s dev-loop13.device
    1.827s dev-loop16.device
    1.824s dev-loop18.device
    1.792s pmcd.service
    1.790s dev-loop9.device
    1.786s dev-loop19.device
    1.651s dev-loop10.device
    1.597s dev-loop20.device
    1.508s xrdp.service
    1.389s dev-loop7.device
    1.389s dev-loop5.device
    1.370s dev-loop6.device
    1.364s dev-loop4.device
    1.363s dev-loop3.device
    1.310s dev-loop2.device
    1.292s pmie.service
    1.264s cloud-init-local.service
    1.235s dev-loop1.device
    1.234s dev-loop0.device
    1.084s cups.service
     996ms networkd-dispatcher.service
     928ms ufw.service
     885ms systemd-journal-flush.service
     720ms winbind.service
     716ms apparmor.service
     704ms snapd.apparmor.service
     662ms nfs-server.service
     584ms bluetooth.service
     577ms avahi-daemon.service
     518ms smbd.service
     512ms cloud-init.service
     486ms thermald.service
     474ms wpa_supplicant.service
     450ms media-ssd.mount
     447ms systemd-logind.service
     444ms cloud-final.service
     432ms cloud-config.service
     365ms systemd-udevd.service
     364ms cockpit-motd.service
     356ms ssh.service
     352ms apport.service
     325ms media-ssd1.mount
     299ms systemd-rfkill.service
     297ms media-usb.mount
     293ms multipathd.service
     290ms plexmediaserver.service
     281ms snap-bare-5.mount
     275ms snap-core18-2796.mount
     275ms kerneloops.service
     273ms xrdp-sesman.service
     271ms snap-core18-2812.mount
     270ms rpcbind.service
     264ms snap-core20-2182.mount
     258ms snap-core20-2264.mount
     256ms user@1000.service
     253ms snap-core22-1033.mount
     248ms snap-core22-1122.mount
     248ms nfs-mountd.service
     244ms grub-common.service
     243ms systemd-tmpfiles-setup.service
     242ms noip2.service
     236ms snap-cups-1041.mount
     225ms snap-cups-1044.mount
     220ms systemd-udev-trigger.service
     217ms snap-firefox-4090.mount
     215ms atd.service
     211ms snap-firefox-4136.mount
     205ms snap-gnome\x2d3\x2d38\x2d2004-140.mount
     202ms pmproxy.service
     201ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
     199ms systemd-timesyncd.service
     194ms systemd-oomd.service
     190ms snap-gnome\x2d42\x2d2204-172.mount
     179ms snap-gnome\x2d42\x2d2204-176.mount
     177ms openvpn.service
     172ms systemd-resolved.service
     169ms snap-gtk\x2dcommon\x2dthemes-1535.mount
     165ms rsyslog.service
     164ms lvm2-pvscan@8:51.service
     158ms snap-lxd-27428.mount
     153ms nfs-idmapd.service
     152ms alsa-restore.service
     150ms modprobe@drm.service
     148ms snap-lxd-27948.mount
     147ms modprobe@configfs.service
     146ms keyboard-setup.service
     143ms modprobe@fuse.service
     138ms lvm2-monitor.service
     137ms snap-snapd-21184.mount
     134ms systemd-fsck@dev-disk-by\x2duuid-ee2ad6ce\x2da9cc\x2d43ec\x2dbf44\x2d50d0f5afba29.service
     133ms sys-kernel-tracing.mount
     133ms kmod-static-nodes.service
     130ms systemd-binfmt.service
     129ms sys-kernel-debug.mount
     129ms snap-snapd-21465.mount
     129ms rpc-statd.service
     128ms systemd-sysusers.service
     125ms proc-fs-nfsd.mount
     123ms dev-mqueue.mount
     123ms snap-ssd\x2dbenchmark-118.mount
     116ms systemd-modules-load.service
     115ms systemd-sysctl.service
     112ms nfsdcld.service
     112ms systemd-remount-fs.service
     109ms dev-hugepages.mount
     107ms var-snap-firefox-common-host\x2dhunspell.mount
     103ms plymouth-read-write.service
     102ms systemd-tmpfiles-setup-dev.service
      96ms packagekit.service
      92ms systemd-networkd.service
      91ms systemd-journald.service
      81ms grub-initrd-fallback.service
      68ms systemd-user-sessions.service
      67ms systemd-update-utmp.service
      64ms console-setup.service
      64ms sys-fs-fuse-connections.mount
      63ms swap.img.swap
      63ms finalrd.service
      61ms proc-sys-fs-binfmt_misc.mount
      60ms sys-kernel-config.mount
      54ms cockpit.socket
      41ms systemd-random-seed.service
      37ms setvtrgb.service
      36ms rpc-statd-notify.service
      33ms run-rpc_pipefs.mount
      18ms nfs-blkmap.service
      18ms pmlogger_check.service
      17ms plymouth-quit.service
      17ms pmie_check.service
      15ms user-runtime-dir@1000.service
      13ms rtkit-daemon.service
      12ms polkit.service
      11ms boot.mount
      11ms pmie_farm.service
       9ms snapd.socket
       8ms pmlogger_farm.service
       8ms modprobe@efi_pstore.service
       7ms systemd-update-utmp-runlevel.service
       4ms pmlogger_farm_check.service
       4ms pmie_farm_check.service
       1ms postgresql.service

```

I changed optional to yes instead of true in netplan and nothing changed, I have disabled wifi already and there no other interfaces. There is something fundamentally wrong which is making 
[TABLE="width: 256"]
[TR]
[TD="colspan: 4"]systemd-networkd-wait-online.service[/TD]
[/TR]
[/TABLE]
take over 2 minutes.

Just to re-iterate, if the system was taking 3 minutes to boot because of things it needed to do then so be it, it's not, it's taking almost 3 minutes to wait for the network interface and from everything in my first post and my config there is no reason it should be.

---

### Post by JayCroghan on 2024-04-21
I have also tried everything here except disabling the service itself: [https://askubuntu.com/questions/972215/a-start-job-is-running-for-wait-for-network-to-be-configured-ubuntu-server-17-1](https://askubuntu.com/questions/972215/a-start-job-is-running-for-wait-for-network-to-be-configured-ubuntu-server-17-1)

---

### Post by #&amp;thj^% on 2024-04-21
Disabling the service will do nothing to help here. Ive tried it previous versions and Usually an update fix's it
```
Details of the Request:
URL: man:NetworkManager-wait-online.service(8)
Protocol: man
Date and Time: Sunday, April 21, 2024 11:03:51 AM MDT
Additional Information: Unknown protocol 'man'.
Description:
The KIO worker which provides access to the man protocol could not be started. This is usually due to technical reasons.
Possible Causes:
klauncher could not find or start the plugin which provides the protocol. This means you may have an outdated version of the plugin.
Possible Solutions:
Update your software to the latest version. Your distribution should provide tools to update your software.
Contact your appropriate computer support system, whether the system administrator, or technical support group for further assistance.
```

I'm sorry to hear you are affected by this annoyance though.

---

### Post by JayCroghan on 2024-04-21
How did you get the details of the problem? I can't figure out anything other than "something is making networkd-wait-online.service" from the literal ocean of things I've read today.

---

### Post by JayCroghan on 2024-04-21
Oh wow, ok, took some jigging, for future travellers, it was a mess of NetworkManager and netplan and networkd all conjoined. I went and followed (or did the bits missing anyway) of these two and it all works perfectly, few seconds reboot :)

[https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd](https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd)

[https://askubuntu.com/questions/1336247/removing-netplan-to-use-systemd-networkd-directly]("https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd")

---

### Post by #&amp;thj^% on 2024-04-21
> **JayCroghan said:**
> Oh wow, ok, took some jigging, for future travellers, it was a mess of NetworkManager and netplan and networkd all conjoined. I went and followed (or did the bits missing anyway) of these two and it all works perfectly, few seconds reboot :)

[https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd](https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd)

[https://askubuntu.com/questions/1336247/removing-netplan-to-use-systemd-networkd-directly]("https://linux.fernandocejas.com/docs/how-to/switch-from-network-manager-to-systemd-networkd")

Nice I'm saving this if it reappears in the future. ;)

Sorry late reply, Ive been outside in some badly needed Vitamin D (SunShine)

> **JayCroghan said:**
> How did you get the details of the problem? I can't figure out anything other than "something is making networkd-wait-online.service" from the literal ocean of things I've read today.

Like this
```
systemctl status  NetworkManager-wait-online.service
&#9675; NetworkManager-wait-online.service - Network Manager Wait Online
     Loaded: loaded (/usr/lib/systemd/system/NetworkManager-wait-online.service>
     Active: inactive (dead)
     _[COLOR="#FF0000"]  Docs: man:NetworkManager-wait-online.service(8)[/COLOR]_

```

---

### Post by JayCroghan on 2024-04-22
Sorry, totally wrong, someone told me change the timeout to 15 seconds and it's just hitting that instead, still timing out at 3 minutes when I remove the 15 second one. So still have this issue.

---

### Post by JayCroghan on 2024-04-22
Sorry, totally wrong, someone told me change the timeout to 15 seconds and it's just hitting that instead, still timing out at 3 minutes when I remove the 15 second one. So still have this issue.

---

### Post by JayCroghan on 2024-04-23
You will not believe this, the way to fix it was to let the *command* finish. I opened the service, copied the file path, which for me was ```
/lib/systemd/systemd-networkd-wait-online
``` and then ran that at bash, it ran and eventually timed out with an error that I didn't take note of because I was stupid and expected it to be the service timeout not remembering I'm not running the damn service, anyway, since then it works totally fine with --any at the command line. Restart the service, call the binary directly, reboot the machione, it all works. Whatever it did when I ran it directly *and let it finish instead of the service timeout ending it early* fixed whatever error it was having.

Please, if you have this error on a machine right now, run the command directly and let me know the error? Some cleanup or some file or something was just needing to happen at the service exit that wasn't happening.

I will write a blog post about this whole episode. I so wish I kept that message :(

---

### Post by vuux on 2024-05-02
I'm having this problem (2-minute timeout during booting of Ubuntu 22.04) on my VPS right now. I've been fighting with this for half a day. Trying to read through tons of noise in this thread. And failing to understand if there is actually a fix here in this thread.

Running the command ( [FONT=lucida console]/lib/systemd/systemd-networkd-wait-online ) manually from bash under root does nothing but hanging for ~2 minutes and **printing exactly the same error message as when run as a service** during boot:
[/FONT]```
root@de:~# /lib/systemd/systemd-networkd-wait-online
Timeout occurred while waiting for network connectivity.
root@de:~# 
```

And adding [FONT=courier new]--timeout=0[/FONT] to the command to disable the timing out just makes the command to hang for 18+ minutes, I didn't see a point to wait more and aborted it with Ctrl-C.

---

### Post by numanair on 2024-08-14
Same problem with a fresh install of 24.04 on some old hardware. Masking the service has had no negative impact and skips the boot wait.

---

