---
title: "What does &quot;-ng&quot; Mean?"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Lateforgym on 2009-03-29
Im trying to learn more about some of the things that I'm typing in to certain utility programs so I can know better what its doing as opposed to following others directions blindly. Here and there I am picking things up but a search on this is dead. So, What does "-ng" mean or is it just a weird naming convention? ex: Airmon-ng eth1

---

### Post by t0p on 2009-03-29
Among the programs you are talking about (airmon-ng, aircrack-ng, airodump-ng) the ng means "next generation" or "new generation" I believe.  The programs airmon, aircrack and airodump have been around a long time, and I think the ng versions are so called because they're the latest and greatest...

Suffixing program names with -ng isn't a naming tradiion that's very widespread. In over 4 years of linux use, I don't think I've seen any programs with the ng suffix other than the aircrack-ng group.

---

### Post by Paqman on 2009-03-29
> **t0p said:**
> In over 4 years of linux use, I don't think I've seen any programs with the ng suffix other than the aircrack-ng group.

EnvyNG?

---

### Post by OutOfReach on 2009-03-29
> **Lateforgym said:**
> Im trying to learn more about some of the things that I'm typing in to certain utility programs so I can know better what its doing as opposed to following others directions blindly. Here and there I am picking things up but a search on this is dead. So, What does "-ng" mean or is it just a weird naming convention? ex: Airmon-ng eth1

It's just be a naming convention.

---

### Post by sandyd on 2009-03-29
> **Paqman said:**
> EnvyNG?
its missing a dash in between envy and ng ;)

---

### Post by t0p on 2009-03-29
> **Paqman said:**
> EnvyNG?

In over 4 years of linux use, I don't think I've seen any programs with the ng suffix other than the aircrack-ng group.  And Envy-ng...

:p

---

### Post by lykwydchykyn on 2009-03-29
It's pretty common:
```
$ apt-cache dump |grep "\-ng"|grep ^Package:
Package: fillets-ng-data                                       
Package: reportbug-ng                                          
Package: lincity-ng-data                                       
Package: fillets-ng                                            
Package: libradiusclient-ng2                                   
Package: lemonldap-ng                                          
Package: linux-wlan-ng-doc                                     
Package: xpilot-ng                                             
Package: linux-wlan-ng-source                                  
Package: libradiusclient-ng-dev                                
Package: xpilot-ng-utils                                       
Package: linux-wlan-ng-modules                                 
Package: aircrack-ng                                           
Package: fprobe-ng                                             
Package: ultrastar-ng-gstreamer                                
Package: xpilot-ng-common
Package: linux-wlan-ng
Package: liblemonldap-ng-manager-perl
Package: fillets-ng-data-cs
Package: liblemonldap-ng-portal-perl
Package: linux-wlan-ng-firmware
Package: fakeroot-ng
Package: ultrastar-ng-xine
Package: liblemonldap-ng-handler-perl
Package: syslog-ng
Package: etpan-ng
Package: ultrastar-ng
Package: xpilot-ng-server
Package: scribus-ng-doc
Package: procinfo-ng
Package: xpilot-ng-client-x11
Package: liblemonldap-ng-conf-perl
Package: scribus-ng
Package: lincity-ng
Package: xpilot-ng-client-sdl
Package: bwm-ng
Package: lemonldap-ng-doc
Package: linux-wlan-ng-0.1.15-modules
Package: apt-cacher-ng

```

---

### Post by RetchingRabbit on 2009-03-29
That's good CLI work, lykwyd. 
Very nice.

---

### Post by LowSky on 2009-03-30
NG stands for Next Generation at least in Envy's case
[http://en.wikipedia.org/wiki/Envy_(software)](http://en.wikipedia.org/wiki/Envy_(software))

Probably stole it form Star Trek: Next Generation, which is ofter abbreviated
ST:NG, or ST-NG

Wow I'm being a nerd

---

