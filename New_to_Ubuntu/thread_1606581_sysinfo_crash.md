---
title: "sysinfo crash"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by phill3006 on 2010-10-26
Whenever I click on system in sysinfo, the program appears to crash.  The window closes (do you still call them windows when you're running linux?) and it ceases to appear in the lower panel.  What's happening?
I'm running a Dell Dimension 3000.  The 2004 model if my math is correct.

---

### Post by stephanvaningen on 2010-10-26
With me the same. Feedback I get from sysinfo is this:
```
GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)
```
What's yours? (You can see it if you first open Terminal (Ctrl+Alt+t) and then just type sysinfo)


(Might be just a bug to inform to the makers of sysinfo...)

---

### Post by beew on 2010-10-26
Same here, but it only crashes when I click "System", if I just want to look at other components it doesn't crash.  If you really want it you may consider downgrading it to the Lucid version.

---

### Post by phill3006 on 2010-10-27
Here's my error nonsense.
"Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)"

---

### Post by grey1beard on 2010-11-12
I'd noticed the same effect of Sysinfo window closing when you clicked on System in my meerkat running with the amd6d version.
If I typed sysinfo in terminal, I only got

GConf.NoSuchKeyException: Key '/apps/sysinfo/window_width' not found in GConf
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo..ctor (System.String[] args) [0x00000] in <filename unknown>:0

None of the "Exception in Gtk# callback delegate...."etc.

John

---

### Post by bradshawd on 2010-12-05
Same here.

Run sysinfo. fine looking at all the other parameters but as soon as I click on System  the app bombs out / disappears.  Output from terminal..

[COLOR="Navy"]bradshawd@Thruxton:~$ sysinfo
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)
[/COLOR]

If anybody has any ideas that would be great

---

### Post by josephellengar on 2010-12-22
me too. only system tab.

---

### Post by albertnet on 2011-01-13
It happened to me as well, once selecting system it would close, so I decided to change settings so the system tab would be the one that shows when it opens and guess what?... Now I'm unable to get it working:confused:
It only opens and closes it immediately, what a disgrace. It happens in both 64 and 32 meerkat flavours. Does anyone knows if there's a command line config to reset it to it's default and see it again? Thank you guys.

By the way, please don't do as I did, it's kinda silly haha.

---

### Post by josephellengar on 2011-01-13
> **bradshawd said:**
> Same here.

Run sysinfo. fine looking at all the other parameters but as soon as I click on System  the app bombs out / disappears.  Output from terminal..

[COLOR="Navy"]bradshawd@Thruxton:~$ sysinfo
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)
[/COLOR]

If anybody has any ideas that would be great


It doesn't look like there is anything that we can do to me. I ran it and got the same output. And since the top part of the call stack is a null reference, that means that the program has some bad exception handling or dangling pointers. That won't work regardless of system configuration. Probably a problem with a specific version of the program. Is everybody else here also on 64 bit?

---

### Post by oldos2er on 2011-01-13
[https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727](https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727)

---

### Post by albertnet on 2011-01-13
Ok guys, so I kept reading and thought to try it as sudo, I did it and the program runs not using the preferences before set as a regular user (I'm the one that changed in preferences the main window to be "system" and then the program wouldn't open), however it still crashes when selecting the System tab. I'm running meerkat 64 & 32, in both the result is the same.
This is the terminal output when running as sudo:

albertnet@Ultron:~$ sudo sysinfo 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo.on_treeview1_cursor_changed(System.Object o, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)



And this is the output as regular user:

albertnet@Ultron:~$ sysinfo
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Sysinfo.SystemInfo.Xorg () [0x00000] in <filename unknown>:0 
  at Sysinfo.Sysinfo.on_notebook1_switch_page (System.Object o, Gtk.SwitchPageArgs e) [0x00000] in <filename unknown>:0 
  at Gtk.Notebook.SwitchPageSignalCallback (IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Notebook.SwitchPageSignalCallback(IntPtr arg0, IntPtr arg1, UInt32 arg2, IntPtr gch)
   at Gtk.Notebook.gtk_notebook_set_current_page(IntPtr , Int32 )
   at Gtk.Notebook.set_CurrentPage(Int32 value)
   at Sysinfo.Sysinfo..ctor(System.String[] args)
   at Sysinfo.Sysinfo.Main(System.String[] args)


Is this of any help?

---

### Post by victorhugo289 on 2011-02-20
I have the same problem in Meerkat, crashing when clicking System.
But the question is: what's supposed to say in System?
The other sections seem to encompass everything a system has. Also I just noticed that in the Welcome screen under Hardware there is a pull-down menu on upper right corner that says "Motherboard", "Graphic Card", "Sound Card", and "Network", that's pretty much all the system to me.

---

### Post by britbrian on 2011-03-22
I had same problem with it crashing on System item
so I followed the thread given above
[https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727](https://bugs.launchpad.net/ubuntu/+source/sysinfo/+bug/596727)

sysinfo_0.7-4_all.deb fixes it and is set for Natty.
You can download it for Meerkat too and it works as expected.
[http://packages.ubuntu.com/natty/all/sysinfo/download](http://packages.ubuntu.com/natty/all/sysinfo/download)

@victorhugo289
The System page just lists:- release name, version #s of GNOME, kernel, GCC, Xorg, hostname & uptime

---

