---
title: "Banshee won't start"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by kmas on 2010-10-02
Ok banshee will not start, it will start but close down after 1 sec. I tried it in the command line, and here is the error i get. 

```
phynx@phynx-HP-Pavilion-dv7-Notebook-PC:~$ banshee-1 %U
[Info  17:36:50.989] Running Banshee 1.8.0: [Ubuntu maverick (development branch) (linux-gnu, x86_64) @ 2010-09-30 23:37:58 UTC]
`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

[Info  17:36:51.857] Updating web proxy from GConf
[Info  17:36:51.931] All services are started 0.793985
`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': banshee-1: undefined symbol: menu_proxy_module_load

(Banshee:7335): Gtk-WARNING **: Failed to load type module: (null)

[Info  17:36:52.697] nereid Client Started

Unhandled Exception: System.ArgumentException: UNC paths should be of the form \\server\share.
  at System.IO.Path.InsecureGetFullPath (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Path.GetFullPath (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.get_FullPath () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileSystemWatcher:get_FullPath ()
  at System.IO.InotifyWatcher.StartDispatching (System.IO.FileSystemWatcher fsw) [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.Start () [0x00000] in <filename unknown>:0 
  at System.IO.FileSystemWatcher.set_EnableRaisingEvents (Boolean value) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) System.IO.FileSystemWatcher:set_EnableRaisingEvents (bool)
  at Banshee.LibraryWatcher.SourceWatcher.Watch () [0x00000] in <filename unknown>:0 

```

I tried to delete the file under ```
~/.config/banshee
```, i deleted the database only, didn't work, deleted the whole folder, didn't work either. Deleted the files under ```
~/.gconf/apps/
``` Uninstalled banshee, purged the files, using bleachbit, then computer janitor, before reinstalling it. Didn't work either. It was previously working, just fired up laptop this morning and it wouldn't work. 

I reinstall glib, mono runtime, but it all didn't work. 
Also tried banshee-1 --play-enqueued %U, didn't work. same errors throughout. 

I can start banshee with sudo, but i don't want to use it like that, i'm worried it might break permissions on files. 

Can someone help please?

---

### Post by directhex on 2010-10-02
This is 1.8.0?

---

### Post by kmas on 2010-10-02
yes it is... sorry i didn't include the version. its on the first few sentences of the error..

---

### Post by andrewthomas on 2010-10-02
Is this from a ppa?

Does the version from the universe repo work?

```
Package: banshee                         
New: yes
State: not installed
Version: 1.7.6-0ubuntu1
```

---

### Post by kmas on 2010-10-02
fix was simple.. 

1- sudo ppa-purge ppa:banshee-team/ppa
2- After ppa-purge, banshee is rolled back to 1.7.6 
3- start banshee, and the problem is temporarily fixed
4- rebuild your library and database <import media>
5- sudo add-apt-repository ppa:banshee-team/ppa
6- issue disappeared.. 

cheers:)

---

### Post by taavipalo on 2010-10-10
I had the same problem and rollback didn't help on my case.

I had to edit gconf manually.
apps -> banshee-1 -> sources -> _music_library_source_-_library -> library-location 
Its value was set to "/" and that caused banshee crashing. Changed it to /home/username/Music and everything was back to normal.

---

### Post by MentatGhola on 2011-12-01
I have tried a number of things here.  Including purging and reinstalling banshee and deleting the .config/banshee-1 file.  

I checked my .gconf/apps/banshee-1/sources/_music_library_source_-_library/library-location file and its already set to /home/username/Music

When I try the command sudo ppa-purge ppa:foo  i get an error saying ppa-purge is an unknown command.  

In case anyone is interested here is my terminal output for running banshee:

```

[Info  13:09:31.155] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-11-10 06:05:59 UTC]

(Banshee:9522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9522): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Width (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.sizeallocated_cb(IntPtr widget, IntPtr allocation)
   at Gtk.Widget.gtksharp_widget_base_show(IntPtr )
   at Gtk.Widget.OnShown()
   at Nereid.PlayerInterface.OnShown()
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

For now I will just switch to amarok

---

### Post by MentatGhola on 2011-12-01
I just tried running with sudo and banshee actually opened for a second before crashing this time.  Here is my output.

```
[Info  13:11:44.327] Running Banshee 2.2.1: [Ubuntu 11.10 (linux-gnu, x86_64) @ 2011-11-10 06:05:59 UTC]

(Banshee:9590): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9590): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9590): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(Banshee:9590): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[Warn  13:11:45.560] DBus support could not be started. Disabling for this session. - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
System.Exception: Unable to open the session message bus. (in `dbus-sharp')
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.Connect (System.String serviceName, Boolean init) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.Connect (System.String serviceName) [0x00000] in <filename unknown>:0 
[Info  13:11:45.988] Migrating album-art cache directory
[Warn  13:11:45.991] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 1: no such table: CoverArtDownloads (SQL: DELETE FROM CoverArtDownloads) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 
[Info  13:11:45.995] Migrated 0 files in 0.005717s
[Info  13:11:46.590] Updating web proxy from GConf
[Warn  13:11:53.561] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  13:11:53.561] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  13:11:53.565] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  13:11:53.565] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.

(Banshee:9590): Gtk-WARNING **: Refusing to add non-unique action 'CloseAction' to action group 'Global'
[Warn  13:11:53.617] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  13:11:53.617] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  13:11:53.617] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  13:11:53.617] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  13:11:53.619] All services are started 8.056264
[Warn  13:11:54.353] Error migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.ValidateDirectoryListing (System.String path, System.String searchPattern, System.Boolean& stop) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  13:11:54.495] AmazonMP3 store redirect URL: https://one.ubuntu.com/music/store/amz/
[Info  13:11:55.110] nereid Client Started
[Info  13:11:55.245] GStreamer version 0.10.35.0, gapless: True, replaygain: False
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_set (intptr,string,intptr,intptr&) <0xffffffff>
  at GConf.Client.SetValue (string,GConf.Value) <0x0003f>
  at GConf.ClientBase.Set (string,object) <0x00047>
  at Banshee.GnomeBackend.GConfConfigurationClient.Set<int> (string,string,int) <0x000b3>
  at Banshee.Configuration.ConfigurationClient.Set<int> (string,string,int) <0x00034>
  at Banshee.Collection.Gui.PersistentColumnController.Set<int> (string,string,int) <0x000eb>
  at Banshee.Collection.Gui.PersistentColumnController.Save (Hyena.Data.Gui.Column,int) <0x0003f>
  at Banshee.Collection.Gui.PersistentColumnController.SaveCore () <0x000a3>
  at Banshee.Collection.Gui.PersistentColumnController.OnTimeout () <0x00027>
  at GLib.Timeout/TimeoutProxy.Handler () <0x0003a>
  at (wrapper native-to-managed) GLib.Timeout/TimeoutProxy.Handler () <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000b>
  at Banshee.Gui.GtkBaseClient.Run () <0x0005f>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00049>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0008e>
  at Banshee.Gui.GtkBaseClient.Startup<T> () <0x0006b>
  at Banshee.Gui.GtkBaseClient.Startup<T> (string[]) <0x000ff>
  at Nereid.Client.Main (string[]) <0x00017>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00047>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00037>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x0006b>
  at Booter.Booter.Main () <0x001db>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

```

---

### Post by MentatGhola on 2011-12-01
ok i should also mention another problem i am having which i assume is related to banshee being integrated into the unity desktop or something but for some reason when I mount an audio cd the disk title and track names aren't recognized.  This didn't happen until i started having the banshee problems.

*edit*  Probably not a desktop thing i guess since I have the same problem under e17 desktop.

---

### Post by MentatGhola on 2011-12-04
[http://ubuntuforums.org/showthread.php?t=1359894](http://ubuntuforums.org/showthread.php?t=1359894)

---

