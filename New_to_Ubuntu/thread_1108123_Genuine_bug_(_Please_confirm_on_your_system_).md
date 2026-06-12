---
title: "Genuine bug? ( Please confirm on your system )"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by ami_nakata on 2009-03-27
I suspect the problems so many people are having with streaming audio/video playback after they applied updates earlier this month might be due to an actual bug that was released at that time in XULrunner, the framework that Mozilla apps are built upon.  I'd appreciate it if people would try to confirm whether their own systems show errors from that update:

(1) Try this in a terminal window to see if your system has missing dependencies/libraries:```
/usr/lib/firefox-3.0.7/run-mozilla.sh `which ldd` -r /usr/lib/xulrunner-1.9.0.7/components/libpyloader.so
``` You're not SUPPOSED to see "not found" errors for libxpcom.so , libxul.so, and libpyxpcom.so , nor six "undefined symbol" errors, according to [https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration](https://developer.mozilla.org/en/Troubleshooting_XPCOM_components_registration) but I bet many or most of you who applied the updates WILL.

(2) In Firefox, compare the results of   ( Tools -->  Add-ons  --> Plug-ins ) to the results obtained by typing ```
about:plugins
``` into Firefox's address bar.  Pay particular attention to the "Default Plugin".  Does the first method say the "Default Plugin" is enabled, while the second method says it's not?

(3) If you run the above would you also please indicate whether you've had any problems with playing streaming audio/video?

If so - as is the case on my Hardy system - might this not interfere with the proper application of additional plugins, like Flash, since facilitating the installation of additional plugins is the purpose of the "Default Plugin"?

If others find the same prolematic results, what do we do about it, submit a bug report in launchpad?  Or is there a satisfacory workaround that will let those of us affected by this get back our ability to use streaming audio & video sites?

Thanks! 

- ami

---

### Post by philinux on 2009-03-27
```
linux-vdso.so.1 =>  (0x00007fffd47fe000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f74cc20f000)
	libxpcom.so => not found
	libxul.so => not found
	libplds4.so.0d => /usr/lib/libplds4.so.0d (0x00007f74cc00a000)
	libplc4.so.0d => /usr/lib/libplc4.so.0d (0x00007f74cbe05000)
	libnspr4.so.0d => /usr/lib/libnspr4.so.0d (0x00007f74cbbc7000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f74cb9c3000)
	libpython2.5.so.1.0 => /usr/lib/libpython2.5.so.1.0 (0x00007f74cb64c000)
	libutil.so.1 => /lib/libutil.so.1 (0x00007f74cb448000)
	libpyxpcom.so => not found
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f74cb13b000)
	libm.so.6 => /lib/libm.so.6 (0x00007f74caeb5000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f74cac9d000)
	libc.so.6 => /lib/libc.so.6 (0x00007f74ca92b000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f74cc645000)
undefined symbol: _ZN14Py_nsISupports21PyObjectFromInterfaceEP11nsISupportsRK4nsIDii	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z16PyXPCOM_LogErrorPKcz	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _ZN14Py_nsISupports21InterfaceFromPyObjectEP7_objectRK4nsIDPP11nsISupportsii	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z24PyXPCOM_MakePendingCallsv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z31PyXPCOM_EnsurePythonEnvironmentv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)
undefined symbol: _Z34PyXPCOM_SetCOMErrorFromPyExceptionv	(/usr/lib/xulrunner-1.9.0.7/components/libpyloader.so)

```

On Intrepid 64 bit and not had any bother streaming anything. Also got the default plugin disabled.

Exactly same results in Jaunty.

---

### Post by philinux on 2009-03-27
Installing libxul-dev improves the not found count. But since I've not had problems streaming I cant see the advantage.

---

### Post by ami_nakata on 2009-03-27
Thanks, Philinux, both for the test and for the word on the libxul-dev. No, no advantage, I think, so long as your system is behaving as it should.  I wonder whether these missing libraries might affect Hardy re audio/video streaming differently, though, as I've been having huge problems trying to get that to work?

I looked around a bit, and the library or (same) "shared object" dependency tree seems to be invalid.  The three "missing" .so files ARE actually present on the system, but they're present in a directory that is *above* the "loader" .so file that I presume calls them, rather than *below* it, as one might more reasonably expect. 

I imagine that represents an error in the package build process, a "disconnect" or "out-of-sync" situation between the loader library and the three libraries it tries to call. If that's so, it would explain why the three never get "registered" even though they're actually present on the system ... just not anywhere the "loader" can find them.

( Does anyone more knowledgeable than I am agree with that diagnosis, and think it merits a launchpad bug report? )

I'm surprised it doesn't affect your installation, Philinux, since XUL and XULrunner are so foundational to Mozilla and thus to Firefox.  You didn't happen to install Firefox from some source outside the "official" Ubuntu one, I suppose, e.g. directly from Mozilla?

OT: Great avatar/icon. Reminds me of a "Homer Simpson" bottle opener someone gave me; it says "Mmmmmmmmm!  Beeeeeeeeeeer!", in Homer's voice when you use it.

---

### Post by philinux on 2009-03-27
> **ami_nakata said:**
> Thanks, Philinux, both for the test and for the word on the libxul-dev. No, no advantage, I think, so long as your system is behaving as it should.  I wonder whether these missing libraries might affect Hardy re audio/video streaming differently, though, as I've been having huge problems trying to get that to work?

I looked around a bit, and the library or (same) "shared object" dependency tree seems to be invalid.  The three "missing" .so files ARE actually present on the system, but they're present in a directory that is *above* the "loader" .so file that I presume calls them, rather than *below* it, as one might more reasonably expect. 

I imagine that represents an error in the package build process, a "disconnect" or "out-of-sync" situation between the loader library and the three libraries it tries to call. If that's so, it would explain why the three never get "registered" even though they're actually present on the system ... just not anywhere the "loader" can find them.

( Does anyone more knowledgeable than I am agree with that diagnosis, and think it merits a launchpad bug report? )

I'm surprised it doesn't affect your installation, Philinux, since XUL and XULrunner are so foundational to Mozilla and thus to Firefox.  You didn't happen to install Firefox from some source outside the "official" Ubuntu one, I suppose, e.g. directly from Mozilla?

OT: Great avatar/icon. Reminds me of a "Homer Simpson" bottle opener someone gave me; it says "Mmmmmmmmm!  Beeeeeeeeeeer!", in Homer's voice when you use it.

Hi glad to help.

Firefox on my Intrepid and Jaunty anr both default ubuntu installs.

---

