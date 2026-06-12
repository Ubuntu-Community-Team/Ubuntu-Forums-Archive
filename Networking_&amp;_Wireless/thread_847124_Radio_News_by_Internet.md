---
title: "Radio News by Internet"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by Alberto2 on 2008-07-02
Hello,
I wanted to listen to the Radio News of [www.radio.rai.it/grr/](www.radio.rai.it/grr/) but a Mozilla Firefox dialog box appeared saying that the RealPlayer 10.5 plugin was needed, so I installed RealPlyer 11 on my Kubuntu 8.04 (1st: libstd++5 and 2nd: the .deb package of RealPlayer 11 3rd: opened it and completed the installation), but things remain as before and the Firefox message asking the RealPlayer plugin still appears (besides I can't follow its installation by Firefox as it makes you download a realplayer .exe (!?) installation file).
What else am I supposed to do in order to make Firefox the RealPlayer application that I have already installed?
Best Regards

---

### Post by cpetercarter on 2008-07-02
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")

---

### Post by Alberto2 on 2008-07-02
> **cpetercarter said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin]("http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin")
Hello,
Thanks a lot. Everything works now! (Even if the last command line gave:
alberto@PC:/usr/lib/firefox-addons/plugins$ sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
mv: impossibile fare stat di `/usr/lib/totem/gstreamer/libtotem-complex-plugin.so': Nessun file o directory)(transation: mv: impossible make stat of ........ no file or directory).
Best Regards

---

