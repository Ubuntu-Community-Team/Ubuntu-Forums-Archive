---
title: "Lucid Bluetooth Nokia 5310"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-06-14
HI, I am fairly new to Ubuntu.

My phone is a Nokia 5310 Express music. After a little trial and error I had bluetooth working and could browse files on the phone and transfer them as well.

Now the device manager can see the phone. Bluetooth is set to visiable on phone. When I try to browse phone I get this error mesage:

Could not display "obex://[00:1D:98:73:40:DA]/".

I tried blueman because the default bluetooth for Lucid also can see the phone but is faded out and I can not click anything.

any help would be appreciated.

---

### Post by Vege 4wd on 2010-06-14
Hi again. I just tried to remove the phone and search for it again. 
when I searched I got this error message:   Adapter is not ready
Traceback (most recent call last):
  File "/usr/bin/blueman-manager", line 222, in inquiry
    self.List.DiscoverDevices()
  File "/usr/lib/python2.6/dist-packages/blueman/gui/DeviceList.py", line 444, in DiscoverDevices
    self.Adapter.StartDiscovery()
  File "/usr/lib/python2.6/dist-packages/blueman/bluez/utils.py", line 28, in warp
    raise errors.parse_dbus_error(exception)
DBusNotReadyError: Adapter is not ready

Not really sure what it all means. Seems it cant communicate with the adaptor.

---

### Post by Vege 4wd on 2010-06-15
Still no joy.

---

### Post by k.sangeeth on 2011-04-27
I was also getting similar errors e.g. the "Blueman Device Manager" for my "Lenovo T61p" gave me a similar error.
To solve the problem I went to menu "Adapter"->"Preferences" and selected the option "Always Visible".
Then I did a "search" again with no problems.

Hope this helps!!!

---

