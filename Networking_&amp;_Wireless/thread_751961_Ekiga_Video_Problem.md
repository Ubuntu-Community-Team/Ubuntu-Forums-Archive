---
title: "Ekiga Video Problem"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by padangbond on 2008-04-11
Hi all,

My company is currently helping implementing IP phones (Grandstream GXV3000) to our clients with Linux environment. Up until now we still have problems receiving video from Ekiga to those phones (GXV3000). The only time we were successful showing videos to those phones were with openwengo on Windows, but this is not an option for us because we require the clients to use Linux and those phones. 

The full environment is as follows:

SIP Server: Asterisk
Clients: Ekiga, Wengo, on Linux.
Videos from GXV shows up in Ekiga, but Ekiga's video doesn't show up at GXV. No audio problems whatsoever, though.

Thanks a lot though, and this is very mission critical (delivering and implementing Ubuntu solutions to clients).

---

### Post by YannickDefais on 2008-04-13
Hi,

I'm surprised to read "Videos from GXV shows up in Ekiga" as the version shipped with Ubuntu only use the H.261 video codec and GXV claims to support H.263 and H.264 video codecs (see: [http://www.grandstream.com/gxv3000.html](http://www.grandstream.com/gxv3000.html) ). Thus this should mean GXV is able to send H.261 video. Or is it Asterisk transcoding the video stream??

As far as I know, Ekiga 2.x can't use video with GXV.

The incoming Ekiga 3.0 will have support for H.264, and the developer in charge of this (Matthias) has a Grandstream GXV3000 and reported success using the H.264 codec.

The Ekiga team (which i'm part of) hope release a BETA of 3.0 in May 2008.

In the mean time, you can try the SVN version (which has the H.264 codec in using the x264 library and the ffmpeg project):
I advice using this script: [http://wiki.ekiga.org/index.php/Compile_your_own_SVN_version_of_Ekiga_on_Ubuntu#Automated_installation_using_a_bash_script](http://wiki.ekiga.org/index.php/Compile_your_own_SVN_version_of_Ekiga_on_Ubuntu#Automated_installation_using_a_bash_script)

[IMG]http://imagebin.ca/img/S0taGpL.png[/IMG]

Or you can try Linphone which has the H263-1998 video codec [http://www.linphone.org/](http://www.linphone.org/) (I'm not sure it will work with H.263, but it is worth the try).

If you want to get in touch with our coders, the best way is to use the mailling list:
[http://ekiga.org/index.php?rub=8](http://ekiga.org/index.php?rub=8)

Best regards,
Yannick

---

