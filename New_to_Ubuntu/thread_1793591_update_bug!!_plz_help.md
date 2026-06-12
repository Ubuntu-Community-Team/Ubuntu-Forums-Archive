---
title: "update bug!! plz help"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Adham.A on 2011-06-29
hello
first before i say my problem I'm very new to Linux and Ubuntu... i really love it ...so far 
second excuse my bad English cause I'm not an English native speaker :)

my Ubuntu is:
11.04 (natty) i368
kernel Linux 2.6.38-8-generic
gnome 2.23.1
two days ago i was apple to download and get software and update... today i got this error:
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened

i rearsh the internet for a solution and i find this to use in terminal:
#sudo rm /var/lib/apt/lists/* -vf
#sudo apt-get update
as i understood it delete the list of update sources then get it again...

i did it but i got this error:

W:GPG error: [http://dl.google.com](http://dl.google.com) stable InRelease: The following signatures were invalid: NODATA 1 NODATA 2, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.


and when i try to update  the same first bug come again
i even tried to use another mirror and restart my PC but nothing work

thank you in advance! I hope you could help me :)

---

### Post by Adham.A on 2011-06-29
so...
i find the solution by my self... 
i depended in this forum...first problem ended when i fixed the second one:

"W:GPG error: [http://dl.google.com]("http://dl.google.com/")  stable InRelease: The following signatures were invalid: NODATA 1  NODATA 2, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ -  Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please  use apt-cdrom to make this CD-ROM recognized by APT. apt-get update  cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386  (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead."
see this post [http://ubuntuforums.org/showthread.php?t=1758383&highlight=Failed+fetch+cdrom%3A%2F%2FUbuntu](http://ubuntuforums.org/showthread.php?t=1758383&highlight=Failed+fetch+cdrom%3A%2F%2FUbuntu)

but i faced another one:

W: GPG error: [http://dl.google.com](http://dl.google.com) stable InRelease: The following signatures were invalid: NODATA 1 NODATA 2

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

what i did is i deleted three lists that caused it in terminal:
#sudo rm /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages
#sudo rm /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
#sudo rm /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en%5fUS

now every thing is up and running
sorry if i wested your time
and thanks because this forum helped me alot

---

### Post by Adham.A on 2011-06-29
sorry i made a mess here lol!!!
i found that if i check the update then the lists will come back!!!
so what i did is go to system setting> update manager>setting>other software and uncheck :
"http://dl.google.com/linux/chrome/deb/ stable main"
what i'm trying to do is if anyone face the same problem will know the solution 
thanks:D

---

### Post by westie457 on 2011-06-29
Hi, Welcome to the fora.

It's good that you found a solution to your problem and posted the steps. It might help others with a similar problem.

Do not be afraid of posting any other problems or queries in the future.

Next time someone might answer you and be able to offer help and advice.

Go on enjoy life with the Ubuntu and Linux experts.

---

### Post by Adham.A on 2011-06-30
thank you!!
this forum is very helpful... you just need to make the right search and ask the right question :)

---

