---
title: "Nautilus 2.24.0 install error--libaries needed(?)"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by xatsmann on 2009-02-05
Hello,

I'm new to Linux--I just installed in on my Dell Dimensions XPS desktop--and I was trying to install Nautilus 2.24.0 and when I run ./configure command I get the following error:

***** WARNING: Building without libstartup-notification
checking pkg-config is at least version 0.9.0... yes
checking for ALL... configure: error: Package requirements (
	bonobo-activation-2.0	>= 2.1.0
	eel-2.0			>= 2.24.0
	glib-2.0		>= 2.17.5
	gnome-desktop-2.0	>= 2.9.91
	gio-unix-2.0
	gio-2.0
	ORBit-2.0		>= 2.4.0
	pango			>= 1.1.2
	gtk+-2.0		>= 2.13.0
	libbonobo-2.0		>= 2.1.0
	libgnome-2.0		>= 2.14.0
	libgnomeui-2.0		>= 2.6.0
	librsvg-2.0		>= 2.0.1
	libxml-2.0		>= 2.4.7
	
) were not met:

No package 'bonobo-activation-2.0' found
No package 'eel-2.0' found
No package 'glib-2.0' found
No package 'gnome-desktop-2.0' found
No package 'gio-unix-2.0' found
No package 'gio-2.0' found
No package 'ORBit-2.0' found
No package 'pango' found
No package 'gtk+-2.0' found
No package 'libbonobo-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'librsvg-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I think I know enough about Linux Ubuntu to know that it is basically asking for these libraries to be installed--my question is there a way to get these all at once or do I have to manually go and find each one and install it? Or is there some command, argument, or environmental variabile that I can set to tell the install script or the kernel (or both) to just go and get these libraries automatically?

Thanks for any help you can give me.

Xatsmann

---

### Post by BlueSkyNIS on 2009-02-05
Tell us why are you installing Nautilus? You installed Ubuntu, right?

---

### Post by xatsmann on 2009-02-05
I wanted a file manager and I didn't see it listed in Applications or Add/Remove programs--are you saying I don't need it? I also thought it would be a good way to learn about how to install a program in Ubuntu.

---

### Post by BlueSkyNIS on 2009-02-05
No, no, no...that is not the right way of doing it. Also, Nautilus is already installed in Ubuntu. It shows up when you click a link in "Places" menu. 

If you want to install a program in Ubuntu you should go through a centralized list of all available programs, which is available if you go in System -> Administration -> Add/Remove software. This is the best and easiest way of doing it. 

You should also really, really read this:
[http://simplyubuntu.wordpress.com/2006/06/27/a-beginners-guide-to-installing-programs-in-ubuntu/](http://simplyubuntu.wordpress.com/2006/06/27/a-beginners-guide-to-installing-programs-in-ubuntu/)

Also here you have more screenshoots:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by xatsmann on 2009-02-05
You are right about Nautlius already being here--I thought it might be since I found some references to using it with Ubuntu but nothing say how to pull it up or find it.

Thanks for the Synaptic Package Manager info--I take it Add/Remove programs is used to simply remove unwanted programs?

---

### Post by BlueSkyNIS on 2009-02-05
And to add programs. This is alternate way of doing it.

---

