---
title: "adjusting the PKG_CONFIG_PATH environment variable"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by allwin12 on 2009-01-22
hi pls help me know how to adjust the PKG_CONFIG_PATH environment variable.

I got this message when i was configuring a package, the command line showed as below


Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... configure: error: Package requirements (libgnomeui-2.0 >= 2.0.0
		 	  gtk+-2.0 	>= 2.6.0
			  gmodule-2.0
			  libglade-2.0 	>= 2.0.0
			  gnome-vfs-2.0
			  gnome-vfs-module-2.0) were not met:

No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'libglade-2.0' found
No package 'gnome-vfs-2.0' found
No package 'gnome-vfs-module-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_CFLAGS
and GNOME_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



What should i do now?

---

### Post by yeats on 2009-01-22
Have you tried installing the requested programs with synaptic or apt-get?  Also - what are you installing, if you don't mind saying?  It's almost always better, especially if you're unfamiliar with installing from source, to install from the repos . . .

---

### Post by snova on 2009-01-22
Install these packages:

[LIST]
[*]libgnomeui-dev
[*]libgtk2.0-dev
[*]libglade2-dev
[/LIST]

And try again. There might be another package or two we need, but I can't find them, so this might be it.

---

