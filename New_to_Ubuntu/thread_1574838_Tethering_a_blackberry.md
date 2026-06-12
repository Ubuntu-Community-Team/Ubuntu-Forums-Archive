---
title: "Tethering a blackberry"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by yoshiki2 on 2010-09-14
Is it possible on ubuntu? using wiki?

---

### Post by basotl on 2010-09-14
Check out Berry4all. It *should* do it. [http://www.berry4all.com/home](http://www.berry4all.com/home)

---

### Post by Komputor on 2010-09-15
> **basotl said:**
> Check out Berry4all. It *should* do it. [http://www.berry4all.com/home](http://www.berry4all.com/home)

  I will say that Berry4all is a VERY user friendly app that does seem to at least work for most OTHER people.  However, I have a different problem.  After installing all of the libs and the pythonwxgtk2.8(for the gui), I ran into this problem:
[code]
Looking for USB devices:
    Bus 003 Device 001: ID 1d6b:0001
    Bus 002 Device 001: ID 1d6b:0001
    Bus 001 Device 004: ID 0fca:8004
    Bus 001 Device 001: ID 1d6b:0002
USB Device lookup finished

Found RIM device (8120)
Exception in thread Thread-6:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
    self.run()
  File "/home/komputor/bbtether (2)/bb_gui.py", line 655, in run
    self.bbtether.start(self.options, self.args)
  File "/home/komputor/bbtether (2)/bb_tether.py", line 84, in start
    berry.read_endpoints(options.interface)
  File "/home/komputor/bbtether (2)/bb_data.py", line 41, in read_endpoints
    bb_usb.read_bb_endpoints(self,interface)
  File "/home/komputor/bbtether (2)/bb_usb.py", line 118, in read_bb_endpoints
    bb_messenging.log("    Manufacturer:"+handle.getString(berry.iManufacturer,100))
USBError: error sending control message: Operation not permitted

If anybody has any kind of insight, please let me know.  I am using a BB curve 8330 -Boost mobile- and Ubuntu 10.04 Lucid.  I know that Boost uses the Sprint 3g network and it should have the same info(other than ONE thing that lets Sprint know that it's a Boost device) as to how it connects to the network, but it just won't connect!

I am not a newbie to linux, nor an expert.  I just don't know what it is that I am missing.  Please excuse me if I am hijacking this thread, but it's the newest thread and I'm quite upset at the lack of support/how to guides from the berry4all site(no matter how well written).

Thanks in advance to anyone that can help me out here :)

---

### Post by yoshiki2 on 2010-09-26
any other options?? easier.. even if i Need to pay..

---

