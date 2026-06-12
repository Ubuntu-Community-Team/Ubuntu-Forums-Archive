---
title: "Graphics drivers on ubuntu 10.10 randomly stopped working"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-11-19
i noticed compiz wasnt working so i went to my desktop effects and it was at none, i then wont to check my graphics driver which said it was enabled. I removed it and went to reinstall, when i click on activate though it asks for my password then says "downloading and installing" for only a few seconds then it dissapears not installing the driver. This is really annoying none of the desktop effects i had now don't work. Anyone had this before?

---

### Post by sikander3786 on 2010-11-19
Can you succesfully update any packages from command line?

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Do these commands list any errors?

And which graphics card is it?

```
lspci | grep VGA
```

---

### Post by Rave Gloves on 2010-11-19
done all of that there and when i tried my hardware drivers again it's doing the same thing, here is the output the the graphics driver.

```
andrew@andrew-R610:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)

```

---

### Post by sikander3786 on 2010-11-19
Did you reboot after removing the drivers? Try to install the drivers after a reboot.

If that doesn't help, start jockey from terminal.

```
jockey-gtk
```

Try to activate the drivers and see if it crashes and returns an error.

---

### Post by Rave Gloves on 2010-11-19
```
andrew@andrew-R610:~$ jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 386, in on_button_toggle_clicked
    'toggle', False):
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 650, in set_handler_enable
    handler_id, enable)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 98, in convert_dbus_exceptions
    return fn(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 90, in dbus_sync_call_signal_wrapper
    raise _h_exception_exc
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.TypeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 337, in _f_result_wrapper
    self._f_result = f()
  File "/usr/share/jockey/handlers/nvidia.py", line 95, in enable
    self._alternatives.set_alternative(nvidia_alternative)
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/alternatives.py", line 89, in set_alternative
    subprocess.check_call([self.__command, '--set', self.__master_link, path])
  File "/usr/lib/python2.6/subprocess.py", line 483, in check_call
    retcode = call(*popenargs, **kwargs)
  File "/usr/lib/python2.6/subprocess.py", line 470, in call
    return Popen(*popenargs, **kwargs).wait()
  File "/usr/lib/python2.6/subprocess.py", line 623, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1141, in _execute_child
    raise child_exception
TypeError: execv() arg 2 must contain only strings

```

here is the error code.

---

### Post by sikander3786 on 2010-11-19
Try reintalling jockey itself.

```
sudo apt-get install --reinstall jockey-gtk
```

You can also install the drivers from command line or Synaptic or Software Center.

```
sudo apt-get install nvidia-current nvidia-common nvidia-settings
```

---

### Post by Rave Gloves on 2010-11-19
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-current is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nvidia-current' has no installation candidate

```

what now?

---

### Post by sikander3786 on 2010-11-19
Go to Software Center > Edit > Software Sources and enable the Restricted Repository.

Then,

```
sudo apt-get update
```

```
sudo apt-get install nvidia-current nvidia-common nvidia-settings
```

---

### Post by Rave Gloves on 2010-11-19
> **sikander3786 said:**
> Go to Software Center > Edit > Software Sources and enable the Restricted Repository.

Then,

```
sudo apt-get update
```

```
sudo apt-get install nvidia-current nvidia-common nvidia-settings
```

thank you so much man, that's my drivers working again, no idea what i must have done to muck them up in the first place!

---

