---
title: "Banshee Won't Start"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by erw314 on 2011-02-03
Whenever I try to start Banshee I get this result:

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Banshee.Gui.GtkBaseClient ---> System.IO.IOException: Disk full. Path /home/eric/.config/banshee-1
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] 
  at Banshee.Base.Paths.get_ApplicationData () [0x00000] 
  at Banshee.Gui.GtkBaseClient..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at Nereid.Client.Main (System.String[] args) [0x00000] 
  at (wrapper managed-to-native) System.AppDomain:ExecuteAssembly (System.Reflection.Assembly,string[])
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly a, System.String[] args) [0x00000] 
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string,System.Security.Policy.Evidence,string[])
  at System.AppDomain.ExecuteAssembly (System.String assemblyFile) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.AppDomain:ExecuteAssembly (string)
  at Booter.Booter.BootClient (System.String clientName) [0x00000] 
  at Booter.Booter.Main () [0x00000] 

Any help on fixing this would be greatly appreciated!

---

### Post by godspeedmav on 2011-02-03
It'd be useful if you tell us what version of Ubuntu and Banshee, you're using.

---

### Post by Thetherumcompound on 2011-02-03
The second line of the error mentions the disk being full then provides a path to a folder in your home directory. How much free space does your hard disk have?

---

### Post by erw314 on 2011-02-04
About 100 MB of disk space free. I'm using Ubuntu 10.10 and Banshee 1.8.

---

### Post by NightwishFan on 2011-02-04
You need to free up more space. Try opening a terminal and running:
```
sudo apt-get clean
```

---

