---
title: "Banshee crashes immediately upon loading"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by herrnaphta on 2010-03-22
Banshee has suddenly started crashing as soon as I try to load it.  I tried uninstalling it and reinstalling it, but no go.  Here's the code it spits out when I try running it through terminal:

```
[Info  18:56:28.288] Running Banshee 1.5.5: [Ubuntu 9.04 (linux-gnu, i486) @ 2010-03-11 20:40:45 UTC]
[Warn  18:56:31.314] Caught an exception - Invalid frame dimensions (in `Hyena.Gui')
  at Hyena.Widgets.AnimatedImage.ExtractFrames () [0x00000] 
  at Hyena.Widgets.AnimatedImage.Load () [0x00000] 
  at Banshee.Gui.Widgets.TaskStatusIcon..ctor () [0x00000] 
[Info  18:56:32.784] All services are started 3.768945s
[Warn  18:56:33.505] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
Marshaling changed signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetException: Object does not match target type.
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.ComboBox.gtk_combo_box_set_active_iter(IntPtr , IntPtr )
   at Gtk.ComboBox.SetActiveIter(TreeIter iter)
   at Banshee.Widgets.DictionaryComboBox`1[[Banshee.Collection.Database.RandomBy, Banshee.Services, Version=1.5.0.0, Culture=neutral, PublicKeyToken=null]].set_ActiveValue(Banshee.Collection.Database.RandomBy value)
   at Banshee.PlayQueue.HeaderWidget..ctor(Banshee.Collection.Database.Shuffler shuffler, System.String shuffle_mode_id, System.String source_name)
   at Banshee.PlayQueue.PlayQueueSource.CreateHeaderWidget()
   at Banshee.PlayQueue.PlayQueueSource.Initialize()
   at Banshee.PlayQueue.PlayQueueSource..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Mono.Addins.TypeExtensionNode.CreateInstance()
   at Banshee.Sources.SourceManager.OnExtensionChanged(System.Object o, Mono.Addins.ExtensionNodeEventArgs args)
   at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged(Mono.Addins.ExtensionNodeEventHandler value)
   at Mono.Addins.ExtensionContext.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Mono.Addins.AddinManager.AddExtensionNodeHandler(System.String path, Mono.Addins.ExtensionNodeEventHandler handler)
   at Banshee.Sources.SourceManager.LoadExtensionSources()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
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
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

```

---

### Post by herrnaphta on 2010-03-23
no advice?

---

