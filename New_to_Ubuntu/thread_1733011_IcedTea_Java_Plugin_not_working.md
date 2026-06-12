---
title: "IcedTea Java Plugin not working"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by jalfor on 2011-04-18
This is what it says:

An unhandlable error occurred

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

When I close that it pops up a thing that says repair and when I click repair it goes white for a second then comes up again.

What do I do?

---

### Post by jalfor on 2011-04-18
bump

---

### Post by Locke_99GS on 2011-04-18
What exactly are you trying to do? Those look like apt problems, which have nothing to do with IcedTea.

---

### Post by jalfor on 2011-04-18
I'me trying to get Java working.

Before I decided to restart my computer it kept saying apt-get was still running but now it just does what I said in the first post.

The message comes up when I press apply changes when I have ticked the IcedTea plugin.

---

### Post by jalfor on 2011-04-18
I don't think I really stated what I wanted very clearly.

I want Java working and I don't care much how.

---

### Post by Locke_99GS on 2011-04-18
I'd start by trying something like this. I doubt that it'll solve the problem, but it'll get us moving in the right direction. Post any erroneous output.

```

sudo apt-get clean
sudo apt-get install -f

```

If they go without a hitch, try installing your package again. Again, please post erroneous output.

---

### Post by jalfor on 2011-04-18
I got to the terms and conditions but I can't see how to accept them. The <OK> button is just text and all the terminal stuff before it seems to have disappeared.

---

### Post by jalfor on 2011-04-18
I just went back to the ice tea thing and clicked repair and it said waiting for apt-get to exit and then I typed

sudo apt-get clean

but it came up with this


joshua@ubuntu:~$ sudo apt-get clean
[sudo] password for joshua: 
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by jalfor on 2011-04-18
...not meaning to sound impatient, but could someone answer please?

---

### Post by jalfor on 2011-04-18
bump

---

### Post by jalfor on 2011-04-18
PLEASE, someone help me

---

### Post by jalfor on 2011-04-18
Whenever I try to do something that involves installing things and stuff it says waiting for apt-get to exit. HELP!!!!!

---

### Post by jalfor on 2011-04-19
Does NOBODY know?

---

### Post by rigel1 on 2011-08-16
I have had trouble with this useless iced-tea java plugin in the past. The simplest solution I find is to uninstall it, then install the the sun-java plugin which I have never had any problems with. Just now I uninstalled iced-tea, as after a system update it ceased to work, ie my java website applets would not load. So I uninstalled it with the following commands from the command prompt:

sudo su (login as root---and it is advisable to shut down firefox or any other web browser)
dpkg -P icedtea6-plugin

then to install the dependable sun-java plugin:

apt-get install sun-java6-plugin

Once the necessary files have been downloaded, you will be prompted to accept the terms and conditions. Just use the "Tab" key to navigate the cursor.

Restart firefox or whatever browser you use, and you will now have functioning java applets like I just did.

Happy surfing :)

---

