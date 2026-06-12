---
title: "BOINC Manager reports no work done"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by lhuppe on 2014-08-21
I have BOINC installed and the Milkyway@home app running. The BOINC Manager reports that the app is running but shows no work done. Has anyone else seen this?

---

### Post by QIII on 2014-08-21
Hi!

How long have you had it running and when was the last time it reported back to the server?

---

### Post by lhuppe on 2014-08-21
It has been running for days now. In advanced mode and under the "Tasks" tab I can see jobs being completed with a status of "Ready to report." To my knowledge this screen has refreshed many times over. Also, under the "Statistics" tab I see a solid red line along the zero axis.

Any thoughts ?

---

### Post by QIII on 2014-08-21
Are there tasks to report that haven't been for several days?

---

### Post by lhuppe on 2014-08-21
I figured it out ... I was wasting my time on vaporware. When I viewed the "Properties" of the Milkyway@home project's application in BOINC Manager it said that Nvidia GPUs are not supported. I went as far as to install the GPUgrid application and that one kept coming back with computation errors. When I saw that it was downloading a CUDA runtime file of unknown origin I killed it off immediately.  According to the BOINC web site both apps have support for Nvidia GPUs. There seems to be an awful lot of bogus information on the net about CUDA hardware and software. I wanted to get BOINC going so that I could contribute. Oh well.

Thank you very much indeed for trying to help.

---

