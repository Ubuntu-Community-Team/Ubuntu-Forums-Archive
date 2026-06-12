---
title: "Rhythmbox, and now Banshee crash on open in 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by zlapidus on 2010-10-16
Hi all, recently did a fresh install of 10.10 after liking 10.04 so much, and I'm having problems.

Rythmbox crashes after being opened, immediately -- there is a little progress bar at the bottom that looks like it's filled up about 10%, and then just is frozen. I've noticed that uninstalling rhythmbox-plugins causes it to open fine, but I like having the album art, last.fm, etc. So, I decided to install Banshee. and after playing fine for about 25 seconds, it now crashes when opened too.

Here's what I see after opening rhythmbox through the terminal:

```

zach@Casaubon:~$ rhythmbox

(rhythmbox:2006): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: pygobject_register_sinkfunc is deprecated (GstObject)

```And here's what banshee says:

```

zach@Casaubon:~$ banshee
[Info  10:22:23.880] Running Banshee 1.7.6: [Ubuntu maverick (development branch) (linux-gnu, x86_64) @ 2010-09-18 21:00:29 UTC]
[Info  10:22:25.043] Updating web proxy from GConf
[Info  10:22:25.128] All services are started 1.057965
[Info  10:22:26.051] nereid Client Started
[Warn  10:22:26.570] Failed to load media-player-info file for 

```at this point it freezes. Then after about 30 seconds i get this lovely volley of messages, as it freezes again:

```
[Warn  10:23:49.443] Failed to load media-player-info file for 
[Warn  10:23:49.443] Failed to load media-player-info file for 
[Warn  10:23:49.443] Failed to load media-player-info file for 
[Warn  10:23:54.702] Failed to load media-player-info file for 
[Warn  10:23:54.702] Failed to load media-player-info file for 
[Warn  10:23:54.777] Failed to load media-player-info file for 
[Warn  10:23:54.777] Failed to load media-player-info file for 
[Warn  10:23:54.778] Failed to load media-player-info file for 
[Warn  10:23:54.778] Failed to load media-player-info file for 
[Warn  10:23:54.778] Failed to load media-player-info file for 
[Warn  10:23:54.778] Failed to load media-player-info file for 
[Warn  10:23:54.779] Failed to load media-player-info file for 
[Warn  10:23:54.779] Failed to load media-player-info file for 
[Warn  10:23:54.780] Failed to load media-player-info file for 
[Warn  10:23:54.780] Failed to load media-player-info file for 
[Warn  10:23:54.789] Failed to load media-player-info file for 
[Warn  10:23:54.803] Failed to load media-player-info file for 

** (Banshee:2018): CRITICAL **: itdb_get_control_dir: assertion `mountpoint' failed
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GLib.MissingIntPtrCtorException: GLib.Object subclass  Hyena.Data.Gui.Accessibility.ListViewAccessible`1[Banshee.Collection.TrackInfo]  must provide a protected or public IntPtr ctor to support wrapping of  native object handles.
  at GLib.ObjectManager.CreateObject (IntPtr raw) [0x00000] in <filename unknown>:0 
  at GLib.Object.GetObject (IntPtr o, Boolean owned_ref) [0x00000] in <filename unknown>:0 
  at GLib.Object.GetObject (IntPtr o) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.get_Accessible () [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[T].AccessibleCellRedrawn (Int32 column, Int32 row) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[T].PaintCell (System.Object item, Int32  column_index, Int32 row_index, Rectangle area, Boolean opaque, Boolean  bold, StateType state, Boolean dragging) [0x00000] in <filename  unknown>:0 
  at Hyena.Data.Gui.ListView`1[T].PaintRow (Int32 row_index, Rectangle  area, StateType state) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[T].PaintList (Rectangle clip) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[T].OnExposeEvent (Gdk.EventExpose evnt) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile,  System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()


```and at this point it crashes. Would love any assistance!

Thanks!

---

### Post by zlapidus on 2010-10-16
Perhaps I should also mention that VLC plays mp3s flawlessly.

---

### Post by zlapidus on 2010-10-16
Ack, I didn't mean to tag this under kubuntu. I should mention that this issue takes place in GNOME; tagging the post as [kubuntu] was an accident. Wish there was a way to edit this.

---

### Post by PaulW2U on 2010-10-16
I share your problem and have similar error messages.

Neither program is of any use to me, both crash at some point or other but I certainly don't get anything like the 25 seconds of audio that you mention. And like you I find that VLC performs very well. I can't remember whether it's banshee or rhythm box but one of them doesn't work in my 10.04 installation either. As I very seldom play any audio or video files, it's not something that I've pursued but I know others have reported similar problems.

---

