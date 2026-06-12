---
title: "Cannot connect to secured (WPA2) wireless"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by onetb on 2007-08-25
While using the guide on [this]("http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring+password") forum thread, I seem to have messed something up with my wireless connectivity.

I am running 7.04 Ubuntu, and I have always been able to get on any wireless network I want, until now...

I was just tired of typing in the keyring password every time I wanted to connect to my secured home wireless connection.  It is a WPA2 secured network on a FON router.  I am still able to connect to the unsecured wireless also being broadcast from the router.  In fact, if I attempt to connect to the secured ssid, it eventually just reconnects me to the unsecured one.

I have reset the router and I know it is not an issue with the router, as I can still connect to the secured ssid with my windows xp machine.

Also probably significant to say, I am using NetworkManager, and it does not detect the secured connection any longer, I have to type in the ssid and passphrase manually.  It then fails.

Please let me know if I haven't covered everything.  I only want to get it back to the way it functioned before, I am not worried any longer about my keyring password, I just want secured wireless connectivity back!

---

### Post by jimrz on 2007-08-25
> **onetb said:**
> While using the guide on [this]("http://ubuntuforums.org/showthread.php?t=463639&highlight=keyring+password") forum thread, I seem to have messed something up with my wireless connectivity.

I am running 7.04 Ubuntu, and I have always been able to get on any wireless network I want, until now...

I was just tired of typing in the keyring password every time I wanted to connect to my secured home wireless connection.  It is a WPA2 secured network on a FON router.  I am still able to connect to the unsecured wireless also being broadcast from the router.  In fact, if I attempt to connect to the secured ssid, it eventually just reconnects me to the unsecured one.

I have reset the router and I know it is not an issue with the router, as I can still connect to the secured ssid with my windows xp machine.

Also probably significant to say, I am using NetworkManager, and it does not detect the secured connection any longer, I have to type in the ssid and passphrase manually.  It then fails.

Please let me know if I haven't covered everything.  I only want to get it back to the way it functioned before, I am not worried any longer about my keyring password, I just want secured wireless connectivity back!

is your router broadcasting the secure essid? at least for me, nm in feisty will not see or connect to any ap that is not broadcast it's essid. although I had no such issue with earlier releases

---

### Post by onetb on 2007-08-26
I have always been able to connect to this ssid in the past, even on Feisty.  Immediately after I tried to eliminate the need to input my keyring everytime, I was still able to see my secured ssid.  It was only after several attempts to connect that my nm stopped seeing it.  I have checked my router config and it is still broadcasting the secured sside

---

