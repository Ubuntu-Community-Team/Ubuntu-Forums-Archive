---
title: "efax and sl-modem (no modem response)"
date: 2004-11-18
forum: Networking &amp; Wireless
---

### Post by irifan on 2004-11-18
Hi all,

i installed my SmartLink modem with the help of the ubuntulinux wiki. Next i did a 
sudo /etc/init.d/sl-modem-daemon restart
with the following output:

Shutting down SmartLink Modem driver normally.
Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


next I run efax-gtk from commandline and update the settings>modem>serial device to ttySL0

when i try to go to standyby the following error occurs:

efax: 36:04 opened /dev/ttySL0
efax: 36:04 Warning: unexpected response "ATQ0V1"
efax: 36:04 Warning: unexpected response "OK"
efax: 36:04 Warning: unexpected response "ATQ0V1"
efax: 36:04 Warning: unexpected response "OK"
efax: 36:04 Error: modem command (&FE&D2S7=120) failed
efax: 36:05 done, returning 3 (invalid modem response)


Any help is much appreciated.  The modem does work under win98. I only need the fax functionality, as i have an DSL internet access.

---

### Post by az on 2004-11-19
What messages do you get when you load the module(s)? (slamr)
sudo tail -f /var/log/messages
and in another terminal load the modules
sudo modprobe slarm


Also, Try using the /dev/modem symlink in case you made a typo.  Try running as root in case you did not give yourself permissions...

If that did not work, maybe I can think of something else.

---

### Post by irifan on 2004-11-22
Hi azz

I am running a german language setting so i have put a rough translition in brackets  [.. ]
here is my tail -f /var/log/messages output:

Nov 22 22:33:23 localhost -- MARK --
Nov 22 22:53:24 localhost -- MARK --
Nov 22 23:13:24 localhost -- MARK --
Nov 22 23:33:25 localhost -- MARK --
Nov 22 23:53:26 localhost -- MARK --
Nov 22 23:55:06 localhost gconfd (root-13555): (Version 2.8.1) wird gestartet (is stating), Prozesskennung [process ID] 13555, Benutzer ]user] »root«
Nov 22 23:55:07 localhost gconfd (root-13555): Die Adresse **[the adress] **»xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle aufgelöst **[resolved at position 0 to a read-only configuration source]**
Nov 22 23:55:07 localhost gconfd (root-13555): Die Adresse »xml:readwrite:/root/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst **[resolved at position 1 to a writable configuration source]**
Nov 22 23:55:07 localhost gconfd (root-13555): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelöst **[resolved at position 2 to a read-only configuration source]**
Nov 23 00:13:27 localhost -- MARK --

Modprobe doesnt do anything:

root@irifan:/ # modprobe slamr
root@irifan:/ #

an lsmod does list slamr:

Module                  Size  Used by
slamr                 376868  2 

tia

---

### Post by az on 2004-11-22
If lsmod does not show the module (slamr or slusb) then it is not loaded.  Is it an amr modem, pci  or a usb modem?  Are you sure that it is a smartlink modem?  

lspci

Try scanmodem from linmodems.org


In one terminal, do
tail -f /var/log/messages

while you load the module in the other
modprobe slamr

since the output you posted seems to include nothing regarding the modem.


Good luck!

---

### Post by irifan on 2004-11-24
here ist my scanModem output:

Providing detail for device at PCI_bus 0000:00:0b.0
  with vendor-ID:device-ID
            ----:----
Class 0703: 2003:8800   Modem: Smart Link Ltd.: Unknown device 8800 (rev 02) (pr og-if 00 [Generic])
  SubSystem 1801:2800   Unknown device 1801:2800
        Flags: bus master, medium devsel, latency 32, IRQ 169
        Memory at dc000000 (32-bit, prefetchable)
        Capabilities: <available only to root>

 SmartLink drivers support this modem:
    2003:8800  SmartLink  SL2800
 But version slmodem-2.9.10 or later is necessary.
 === Checking PCI IDs through chipset providers and modem assemblers ====
grep: /etc/modprobe.conf: Datei oder Verzeichnis nicht gefunden
grep: /etc/modprobe.conf: Datei oder Verzeichnis nicht gefunden



the solution ist already included, i think: i need the 2.9.10 version and ubtuntu has only 2.9.9 packages. I checked the horay repos (its installed for testing purposes on an extra partition) and it has not been updated. in fact i could not find any .deb for 2.9.10 at google.

compiling from source does not work the easy way (conigure, make, make install ), so i guess i rather be patient and wait a bit untill the updated packages are in the repo.

---

