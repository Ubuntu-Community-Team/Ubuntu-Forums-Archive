---
title: "Banshee Media Player Starts then Crashes"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Chris Donahoe on 2010-12-15
I'm running Ubuntu 10.04 LTS and recently upgraded Banshee Media Player which I had been using for months no problem. I'm not sure what version I was using before and I'm not sure what version I'm using now. I assume 1.8.0 or higher. Here's what I get when I type 'banshee' into the terminal:

[Info  13:12:49.932] Running Banshee 1.9.1: [Ubuntu 10.04.1 LTS d5f5788 (linux-gnu, i486) @ 2010-12-15 16:50:09 UTC]
[Warn  13:12:52.464] BansheeAwn - Failed loading Awn Extension.  - System.Exception: org.freedesktop.DBus.Error.ServiceUnknown: The name com.google.code.Awn was not provided by any .service files (in `NDesk.DBus.Proxies')
  at Banshee.Awn.IAvantWindowNavigatorProxy.UnsetTaskIconByName (System.String TaskName) [0x00000] 
  at Banshee.Awn.AwnService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
[Info  13:12:52.534] Updating web proxy from GConf
[Info  13:12:52.594] All services are started 2.404954
[Info  13:12:53.607] nereid Client Started
[Info  13:12:53.927] AppleDeviceSource is ignoring unmounted volume sda3
[Warn  13:12:53.928] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:53.936] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:53.939] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.021] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000] 
  at Banshee.Dap.MassStorage.MassStorageSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Info  13:12:54.022] AppleDeviceSource is ignoring unmounted volume sda2
[Warn  13:12:54.022] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.023] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.029] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.030] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000] 
  at Banshee.Dap.MassStorage.MassStorageSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Info  13:12:54.100] AppleDeviceSource is ignoring unmounted volume sda1
[Warn  13:12:54.100] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.104] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.105] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.IsKarma (IDevice dev) [0x00000] 
  at Banshee.Dap.Karma.KarmaSource.DeviceInitialize (IDevice dev) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.105] Caught an exception - System.ArgumentNullException: Argument cannot be null. (in `mscorlib')
  at System.Int32.Parse (System.String s, NumberStyles style, IFormatProvider provider) [0x00000] 
  at System.Int32.Parse (System.String s, NumberStyles style) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetVendorId (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_VendorId () [0x00000] 
  at Banshee.Dap.MassStorage.DeviceMapper.Map (Banshee.Dap.MassStorage.MassStorageSource source) [0x00000] 
  at Banshee.Dap.MassStorage.MassStorageSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
[Warn  13:12:54.121] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: s (in `mscorlib')
  at System.Int32.Parse (System.String s) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.GetBusNumber (IUsbDevice device) [0x00000] 
  at Banshee.Hardware.Gio.UsbDevice.get_BusNumber () [0x00000] 
  at Banshee.Hardware.Gio.Device.ResolveUsbPortInfo () [0x00000] 
  at Banshee.Dap.Mtp.MtpSource.DeviceInitialize (IDevice device) [0x00000] 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IndexOutOfRangeException: Array index is out of range.
  at Hyena.Widgets.SimpleTable`1[Banshee.Dap.DapLibrarySync].InsertRow (Banshee.Dap.DapLibrarySync item, UInt32 row, Gtk.Widget[] cols) [0x00000] 
  at Hyena.Widgets.SimpleTable`1[Banshee.Dap.DapLibrarySync].AddRow (Banshee.Dap.DapLibrarySync item, Gtk.Widget[] cols) [0x00000] 
  at Banshee.Dap.Gui.DapContent.AddLibrary (Banshee.Dap.DapLibrarySync library_sync) [0x00000] 
  at Banshee.Dap.Gui.DapContent.BuildWidgets () [0x00000] 
  at Banshee.Dap.Gui.DapContent..ctor (Banshee.Dap.DapSource source) [0x00000] 
  at Banshee.Dap.DapSource.<Initialize>m__F () [0x00000] 
  at Banshee.ServiceStack.Application+<Invoke>c__AnonStorey27.<>m__43 () [0x00000] 
  at Banshee.Gui.GtkBaseClient+<RunIdle>c__AnonStorey1D.<>m__9F () [0x00000] 
  at GLib.Idle+IdleProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
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
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

---

### Post by Chris Donahoe on 2010-12-16
Update: The player only crashes when I have my external harddrive mounted. Banshee will open and stay open as long as I don't have my HD mounted. As soon as I mount it, the program crashes.

---

### Post by Chris Donahoe on 2010-12-16
solved:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1629453](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1629453)

---

### Post by Chris Donahoe on 2010-12-18
Sorry, this did not solve the problem. I think it is a problem related to cpu usage. Please help!!

---

