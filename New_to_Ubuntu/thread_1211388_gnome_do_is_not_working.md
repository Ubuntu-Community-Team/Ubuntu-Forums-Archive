---
title: "gnome do is not working"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Vichfret on 2009-07-12
Hi, gnome do doesn't start, when I run it in a terminal I get this:

```
vicfred@Maggie:~$ gnome-do

** (Do:19878): WARNING **: The following assembly referenced from /usr/lib/gnome-do/Do.Platform.Linux.dll could not be loaded:
     Assembly:   gnomedesktop-sharp    (assemblyref_index=10)
     Version:    2.20.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/gnome-do).


** (Do:19878): WARNING **: Could not load file or assembly 'gnomedesktop-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.ExtensionNodeEventArgs.get_ExtensionObject () [0x00000] 
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Fatal 13:14:01.781] [Services] Service of type AbstractSystemService not found. Using default service instead.
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.TypeLoadException: Could not load type 'Do.Platform.Linux.SystemService' from assembly 'Do.Platform.Linux, Version=0.9.0.0, Culture=neutral, PublicKeyToken=null'.
  at (wrapper managed-to-native) System.MonoType:GetConstructors_internal (System.Reflection.BindingFlags,System.Type)
  at System.MonoType.GetConstructors (BindingFlags bindingAttr) [0x00000] 
  at System.MonoType.GetConstructorImpl (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Type.GetConstructor (BindingFlags bindingAttr, System.Reflection.Binder binder, CallingConventions callConvention, System.Type[] types, System.Reflection.ParameterModifier[] modifiers) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

** (Do:19878): WARNING **: Could not load file or assembly 'gnomedesktop-sharp, Version=2.20.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Stacktrace:


Native stacktrace:

    /usr/bin/cli [0x806d944]
    /usr/bin/cli [0x808616b]
    [0xb80d2410]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7e1c6e0 (LWP 19878)]
[New Thread 0xb6301b90 (LWP 19883)]
[New Thread 0xb7636b90 (LWP 19880)]
[New Thread 0xb765ab90 (LWP 19879)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb80d2430 in __kernel_vsyscall ()
  4 Thread 0xb765ab90 (LWP 19879)  0xb80d2430 in __kernel_vsyscall ()
  3 Thread 0xb7636b90 (LWP 19880)  0xb80d2430 in __kernel_vsyscall ()
  2 Thread 0xb6301b90 (LWP 19883)  0xb80d2430 in __kernel_vsyscall ()
  1 Thread 0xb7e1c6e0 (LWP 19878)  0xb80d2430 in __kernel_vsyscall ()

Thread 4 (Thread 0xb765ab90 (LWP 19879)):
#0  0xb80d2430 in __kernel_vsyscall ()
#1  0xb7fe68f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7fdf4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7f3449e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb7636b90 (LWP 19880)):
#0  0xb80d2430 in __kernel_vsyscall ()
#1  0xb7fe30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x081833b5 in ?? ()
#10 0xb7fdf4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7f3449e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb6301b90 (LWP 19883)):
#0  0xb80d2430 in __kernel_vsyscall ()
#1  0xb7fe60fb in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0806da5e in ?? ()
#3  0x0808616b in ?? ()
#4  <signal handler called>
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 1 (Thread 0xb7e1c6e0 (LWP 19878)):
#0  0xb80d2430 in __kernel_vsyscall ()
#1  0xb7fe5cf9 in __lll_lock_wait () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7fe1138 in _L_lock_289 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7fe0b76 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x081b1a50 in ?? ()
#5  0x0807029f in ?? ()
#6  0xb7ce2066 in ?? ()
#7  0xb633552e in ?? ()
#8  0xb633526e in ?? ()
#9  0xb633523b in ?? ()
#10 0xb6335226 in ?? ()
#11 0xb6335164 in ?? ()
#12 0xb7a2f40e in ?? ()
#13 0xb7a2f1b3 in ?? ()
#14 0x080bad75 in mono_runtime_exec_main ()
#15 0x080bb4eb in mono_runtime_run_main ()
#16 0x0805c917 in mono_main ()
#17 0x0805ac62 in ?? ()
#18 0xb7e66775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#19 0x0805aba1 in ?? ()
#0  0xb80d2430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

How do I fix it?

---

### Post by wojox on 2009-07-12
What happens when you :


```
startx
```

---

### Post by OutOfReach on 2009-07-12
Hmm...I'm not too sure, but it looks like it's not finding the gnome C# bindings...
Go to System>Administration>Synaptic and search for gnome-desktop-sharp2 and check if that package is installed

---

### Post by Vichfret on 2009-07-12
@wojox
```

vicfred@Maggie:~$ sudo startx


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```
[LEFT]@OutFfReach
Yes, it's installed
[/LEFT]

---

### Post by directhex on 2009-07-12
> **Vichfret said:**
> @wojox
```

vicfred@Maggie:~$ sudo startx


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```
[LEFT]@OutFfReach
Yes, it's installed
[/LEFT]

Which version? It sounds to me like you're on Jaunty but have Do for Intrepid

---

### Post by Vichfret on 2009-07-13
> **directhex said:**
> Which version? It sounds to me like you're on Jaunty but have Do for Intrepid

GNOME Desktop# 2.24 suite, CLI bindings for GNOME
Gnome Do version is 0.8.1.3-0ubuntu2(jaunty)

And yes, I'm on Jaunty

---

### Post by directhex on 2009-07-13
Reinstall the package - if it wants GNOME# 2.20, it's not built for Jaunty

---

### Post by yogeshg1987 on 2009-08-03
I'm having the same problem, i.e. cant start gnome-do;

Here's the error message i'm getting:

```
yogesh@yogesh-laptop:~$ gnome-do

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Stdlib ---> System.DllNotFoundException: libMonoPosixHelper.so
  at (wrapper managed-to-native) Mono.Unix.Native.Stdlib:GetDefaultSignal ()
  at Mono.Unix.Native.Stdlib..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Unix.UnixMarshal.AllocHeap (Int64 size) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, Int32 index, Int32 count, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s, System.Text.Encoding encoding) [0x00000] 
  at Mono.Unix.UnixMarshal.StringToHeap (System.String s) [0x00000] 
  at Mono.Unix.Catalog.MarshalStrings (System.String s1, System.IntPtr& p1, System.String s2, System.IntPtr& p2, System.String s3, System.IntPtr& p3) [0x00000] 
  at Mono.Unix.Catalog.Init (System.String package, System.String localedir) [0x00000] 
  at Do.Do.Main (System.String[] args) [0x00000] 
yogesh@yogesh-laptop:~$ 
```

Please Help

---

### Post by directhex on 2009-08-03
aptitude reinstall libmono0

However, your error has nothing to do with the OP's error - you shouldn't recycle help threads for different problems

---

