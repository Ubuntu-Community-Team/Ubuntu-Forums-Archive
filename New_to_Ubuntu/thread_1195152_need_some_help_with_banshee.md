---
title: "need some help with banshee"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Def_101 on 2009-06-23
was using banshee last night to organize my music get cover art. this morning installed a gstreamer codec to veiw an email video, then went to go into banshee computer froze and i haven't been able to open banshee again. i get the wait symbol and it says banshe is starting on the bottom, but nothing. i removed the codec i installed today and nothing i reinstalled banshee and nothing a little help would be appreciated thanx

---

### Post by Def_101 on 2009-06-23
on running banshee-1 this is what i get

at Mono.Addins.Serialization.BinaryXmlReader.Skip () <0x00055>
  at Mono.Addins.Serialization.BinaryXmlReader.SkipToValue (string) <0x0007c>
  at Mono.Addins.Serialization.BinaryXmlReader.ReadValue (string) <0x00011>
  at Mono.Addins.Database.FileDatabase.ReadObject (string,Mono.Addins.Serialization.BinaryXmlTypeMap) <0x0004a>
  at Mono.Addins.Database.AddinHostIndex.Read (Mono.Addins.Database.FileDatabase,string) <0x00018>
  at Mono.Addins.Database.AddinDatabase.GetAddinHostIndex () <0x00070>
  at Mono.Addins.Database.AddinDatabase.GetAddinForHostAssembly (string,string) <0x00077>
  at Mono.Addins.AddinRegistry.GetAddinForHostAssembly (string) <0x0003d>
  at Mono.Addins.AddinSessionService.CheckHostAssembly (System.Reflection.Assembly) <0x00089>
  at Mono.Addins.AddinSessionService.ActivateRoots () <0x0004f>
  at Mono.Addins.AddinSessionService.Initialize () <0x00026>
  at Mono.Addins.AddinManager.Initialize (string) <0x00156>
  at Banshee.ServiceStack.ServiceManager.InitializeAddins () <0x00049>
  at Banshee.ServiceStack.ServiceManager.DefaultInitialize () <0x0000c>
  at Banshee.ServiceStack.Application.Initialize () <0x00007>
  at Banshee.Gui.GtkBaseClient.Initialize (bool) <0x0001a>
  at Banshee.Gui.GtkBaseClient..ctor (bool,string) <0x00026>
  at Banshee.Gui.GtkBaseClient..ctor () <0x00019>
  at Nereid.Client..ctor () <0x0000d>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void__this__ (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0x00004>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod.InternalInvoke (object,object[],System.Exception&) <0xffffffff>
  at System.Reflection.MonoCMethod.Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x000bd>
  at System.Reflection.MonoCMethod.Invoke (System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x0001c>
  at System.Reflection.ConstructorInfo.Invoke (object[]) <0x00035>
  at System.Activator.CreateInstance (System.Type,bool) <0x000f7>
  at System.Activator.CreateInstance (System.Type) <0x0000c>
  at Banshee.Gui.GtkBaseClient.Startup () <0x0000f>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00038>
  at Banshee.Gui.GtkBaseClient.Startup (string[]) <0x000b9>
  at Nereid.Client.Main (string[]) <0x0000a>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    mono [0x806d944]
    [0xb7ffb410]
    /lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7daa098]
    mono [0x81868be]
    [0xb7ffb410]
    mono [0x815146e]
    mono [0x8152812]
    mono [0x80fc536]
    [0xb7198023]
    [0xb7197f68]
    [0xb64a21cb]
    [0xb64a20b4]
    [0xb64a1fc8]
    [0xb64a9b0a]
    [0xb64a9b16]

---

### Post by Def_101 on 2009-06-23
complete uninstall (backed up library since i put a ot of time into it) then reinstall

---

