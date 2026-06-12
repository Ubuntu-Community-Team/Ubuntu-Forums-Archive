---
title: "Can't switch AR9285 Wireless Network Adapter into monitormode."
date: 2010-10-30
forum: New to Ubuntu
---

### Post by Sfekke on 2010-10-30
Hi all,


First of all i'd like to point out that i'm brand new at Linux-systems. I   had my install done yesterday and i'm loving it so far.
Since last night i've been looking up how to switch my AR9285 Wireless Network Adapter into monitormode.
I've found the patching commands ; 

    [SIZE=1][COLOR=Blue]PaulFertser> Get _your_ country code from regd.h, add 32768 and supply as a parameter.
[EMAIL="fercerpav@gmail.com"]fercerpav@gmail.com[/EMAIL]
--- linux-2.6.32-gentoo-r1-orig/drivers/net/wireless/ath/ath9k/main.c    2009-12-03 06:51:21.000000000 +0300
+++ linux-2.6.32-gentoo-r1/drivers/net/wireless/ath/ath9k/main.c    2010-01-16 02:04:00.000000000 +0300
@@ -28,6 +28,11 @@
 module_param_named(nohwcrypt, modparam_nohwcrypt, int, 0444);
 MODULE_PARM_DESC(nohwcrypt, "Disable hardware encryption");

+static int modparam_override_eeprom_regdomain = -1;[/COLOR][/SIZE] [SIZE=1][COLOR=Blue]
+module_param_named(override_eeprom_regdomain, 
+      modparam_override_eeprom_regdomain, int, S_IRUGO);
+MODULE_PARM_DESC(override_eeprom_regdomain, "Override regdomain hardcoded in EEPROM with this value (DANGEROUS).");
+
 /* We use the hw_value as an index into our private channel structure */

 #define CHAN2G(_freq, _idx)  { \[/COLOR][/SIZE] [SIZE=1][COLOR=Blue]
@@ -1588,6 +1593,14 @@
  if (error != 0)
   return error;

+    if (modparam_override_eeprom_regdomain != -1) {[/COLOR][/SIZE] [SIZE=1][COLOR=Blue]
+     printk(KERN_ERR "ath9k: DANGER! You're overriding EEPROM-defined regulatory domain.\n");
+     printk(KERN_ERR "ath9k: Your card was not certified to operate on the domain you choosed.\n");
+     printk(KERN_ERR "ath9k: This might result in a violation of your local regulatory rules.\n");
+     printk(KERN_ERR "ath9k: Do not ever do that unless you really know what you do!\n");
+     sc->common.regulatory.current_rd = modparam_override_eeprom_regdomain;
+    }
+
  /* get mac address from hardware and set in mac80211 */

[/COLOR][/SIZE] [SIZE=1][COLOR=Blue]  SET_IEEE80211_PERM_ADDR(hw, sc->sc_ah->macaddr);
[/COLOR][/SIZE]
    
but what i can't find so far is how to get this patch actually changing my driver ? :/
Pls help me. Keep in mind, total Linux-newb here.

ty,
Sfekke

---

### Post by lisati on 2010-10-30
Duplicate of [http://ubuntuforums.org/showthread.php?t=1609326](http://ubuntuforums.org/showthread.php?t=1609326)

---

