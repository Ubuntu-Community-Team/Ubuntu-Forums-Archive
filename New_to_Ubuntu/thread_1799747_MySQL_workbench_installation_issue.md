---
title: "MySQL workbench installation issue"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by vmayank on 2011-07-08
Hi All,

I am facing a few problems installing mysql workbench. I installed ubuntu 9.10 and PHP.
I downloaded the deb file -
mysql-workbench-gpl-5.2.34-1ubu1004-i386.deb

 and ran it. It completed and then gave an error:
libatk1.0-0

I checked a few forums and then realised that the package manager is already showing libatk1.0-0 as installed.

I think my computer guy may have already installed mysql and I have somehow corrupted it.

The mysql workbench is not showing up in the applications panel but i can access it through the terminal.

I tried the mysql_install_db command which gives the error:
ERROR: 1017  Can't find file: './mysql/db.frm' (errno: 13)

Apologies, I am a newbie and so may not be giving the right information.
Please help me

Thanks
Mayank

---

### Post by dasan on 2011-07-08
It seems like U have mysql workbench installed already 
If you think that there are unwanted packages in the system you can use
sudo apt-get autoremove to remove the package 

and you can always edit the start menu or create an application launcher to make an entry for opening workbench

---

### Post by vmayank on 2011-07-08
managed to sort it that issue out. But have a new one - basically had to do remove mysql and then re-install it. Some dependencies were also missing, that have been resolved.

Now, I have a new problem at hand. When I try to make the installer using
make -j3 install, i get the following error. I have no idea what this means!!! can someone help?

diff/grtdiff.cpp:157: error: ‘stricmp’ was not declared in this scope
make[3]: *** [grtdiff.lo] Error 1
make[3]: *** Waiting for unfinished jobs....
mv -f .deps/python_context.Tpo .deps/python_context.Plo
mv -f .deps/grtpp_module_python.Tpo .deps/grtpp_module_python.Plo
make[3]: Leaving directory `/home/user/Downloads/mysql-workbench-gpl-5.1.19-src/library/grt/src'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/user/Downloads/mysql-workbench-gpl-5.1.19-src/library/grt'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/user/Downloads/mysql-workbench-gpl-5.1.19-src/library'
make: *** [install-recursive] Error 1

---

