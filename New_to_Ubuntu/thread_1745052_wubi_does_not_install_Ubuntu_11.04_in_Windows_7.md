---
title: "wubi does not install Ubuntu 11.04 in Windows 7"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by rocketcount on 2011-04-30
On [www.ubuntu.com]("http://www.ubuntu.com") they say:
 
If you’ve got Windows, you can run Ubuntu within your current system with the Windows installer (Wubi). That way, you can install and uninstall Ubuntu in the same way as any other Windows application. It's simple and safe.
 
But when I download Wubi (Ubuntu 11.04) and run it, pyrun.exe starts and it installs Ubuntu 11.04 amd64 besides my Windows 7 and not like any other Windows application like it says on their website.
 
When I reboot there is a Boot Manager which should not be there as I am only using Windows.
 
Am I doing something wrong here?

---

### Post by lisati on 2011-04-30
Wubi works somewhere in between a "dual boot" and a regular Windows application. It sets up Ubuntu in a folder on your Windows partition in such a way that you can remove Ubuntu via the Add/Remove programs option in Windows. Ubuntu doesn't actually run as a Windows application, it's an operating system in its own right: when you boot your computer you have a choice between starting Ubuntu and Windows.

---

