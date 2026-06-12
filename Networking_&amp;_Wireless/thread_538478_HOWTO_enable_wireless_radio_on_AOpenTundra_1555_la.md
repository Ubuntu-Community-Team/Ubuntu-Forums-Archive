---
title: "HOWTO enable wireless radio on AOpen/Tundra 1555 laptop"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by noob12 on 2007-08-30
This laptop is sold under both the AOpen and Tundra brand names.  The 1555 model has an Intel Pro Wireless 2100 ethernet and a set of "launchpad" hotkey buttons, one of which is supposed to control enabling/disabling the wireless radio.

This has been used successfully by a few other users with Ubuntu kernel 2.6.20-16 (which comes with version 0.5.34 of the acerhk module).  I am not sure it works in earlier versions.

This HOWTO applies to you (only) if you have this model of laptop and you are unable to enable the wireless radio.  You can confirm this condition by checking whether you see messages like the following in your **dmesg** output.

```

[  167.308000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  167.440000] eth1: Radio is disabled by RF switch.

```
and if the command
```

cat /sys/class/net/*/device/rf_kill

```
shows the value 2.

To fix, run this command.  Cut and paste is suggested to avoid errors transcribing.
```

echo "acerhk poll=1 autowlan=1" | sudo tee -a /etc/modules

```

Then reboot.

After reboot, pressing the wireless hotkey button should work for you to enable and disable the wireless radio.

After enabling the radio with the button, you should be able to see that
```

cat /sys/class/net/*/device/rf_kill

```
no longer shows a 2.

If you have additional problems with your wireless connection after enabling the radio, please start a new thread.  This HOWTO only applies to getting the radio enabled.

For users of other Acer and AOpen laptops with Intel Pro Wireless devices in them, you may find the following references useful.

[http://ipw2100.sourceforge.net/index.php](http://ipw2100.sourceforge.net/index.php) (and the other ipw sites there).
[http://rfswitch.sourceforge.net/](http://rfswitch.sourceforge.net/)
[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)

---

