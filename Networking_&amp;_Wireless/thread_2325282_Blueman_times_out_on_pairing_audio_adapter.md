---
title: "Blueman times out on pairing audio adapter"
date: 2016-05-20
forum: Networking &amp; Wireless
---

### Post by BA3MtEP on 2016-05-20
I have a Logitech bluetooth audio adapter to connect my computer to my Hifi. (Ubuntu 14.04)

It suddenly stopped working and I couldn't connect to audio.

I removed the device in blueman and tried pairing from scratch but now keep getting a timeout error.

I ran blueman in a terminal and went through the pairing procedure and got the shown below.
Any advice appreciated.

on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:148)
adapter propery changed Discovering 0 
_________
err (/usr/bin/blueman-manager:226)
(DBusException(dbus.String(u'Connection Timeout'),),) 
_________
on_property_changed (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:148)
adapter propery changed Devices dbus.Array([dbus.ObjectPath('/org/bluez/779/hci0/dev_98_0D_2E_51_41_F6'), dbus.ObjectPath('/org/bluez/779/hci0/dev_1C_39_47_47_3B_90')], signature=dbus.Signature('o'), variant_level=1) 
_________
RemoveDevice (/usr/lib/python2.7/dist-packages/blueman/gui/DeviceList.py:420)
<Device object at 0xa075c8c4 (blueman+main+Device+Device at 0x98d24c0)> 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:89)
invalidating device /org/bluez/779/hci0/dev_FC_58_FA_8F_2A_38 
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:67)
deleting device /org/bluez/779/hci0/dev_FC_58_FA_8F_2A_38 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:89)
invalidating device /org/bluez/779/hci0/dev_FC_58_FA_8F_2A_38 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:165)
HTC 
_________
Generate (/usr/lib/python2.7/dist-packages/blueman/gui/manager/ManagerDeviceMenu.py:165)
HTC 
/usr/lib/python2.7/dist-packages/gi/overrides/__init__.py:92: Warning: Source ID 3813 was not found when attempting to remove it
  return fn(*args, **kwargs)
_________
__del__ (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:67)
deleting device None 
_________
Destroy (/usr/lib/python2.7/dist-packages/blueman/main/Device.py:89)
invalidating device None

---

### Post by jeremy31 on 2016-05-21
Does it work if you use the regular bluetooth manager instead of blueman?

---

### Post by BA3MtEP on 2016-05-21
No it didn't. But - I tried it again this morning after unplugging the adapter from the power overnight, and hey presto it just started working again. No idea what went wrong but unplugging/plugging in again seems to be the solution.

Thanks anyway

---

