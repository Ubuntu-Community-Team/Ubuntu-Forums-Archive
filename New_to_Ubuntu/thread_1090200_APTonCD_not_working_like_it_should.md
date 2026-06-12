---
title: "APTonCD not working like it should"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by longtom on 2009-03-08
Hi,

When I use APTonCD on my mothermachine and try to install on one of the offline PCs, I can:

1.
not restore but have to use Synaptic

2.
When I do so I have a lot of packages searching for dependencies which are not on the cd.
Example:

Cannot install Blender looking for
libftgl2
....
.....

etc

Any ideas what I can do to avoid this?

Any other way I can have all my packages on a DVD for installation on offline machines (preferably even able to choose between packages?

Any suggestions welcome.

Thank you

longtom

---

### Post by sanus|art on 2009-03-08
You can try '[remastersys]("http://www.klikit-linux.com/projects/remastersys/ubuntu.html")' - it is a fast live CD creation with a great option to save user info along with it.
AptOnCD is only getting the *.deb files from `/var/cache/apt/archives`.

---

### Post by longtom on 2009-03-08
> **sanus|art said:**
> You can try '[remastersys]("http://www.klikit-linux.com/projects/remastersys/ubuntu.html")' - it is a fast live CD creation with a great option to save user info along with it.
AptOnCD is only getting the *.deb files from `/var/cache/apt/archives`.

Thanks - tried that and don't get it installed.  It just doesn't appear in synaptic after following the instructions...

longtom

---

### Post by sanus|art on 2009-03-08
Weird? Maybe this:
```

echo "deb http://www.remastersys.klikit-linux.com/repository remastersys/"  |  sudo tee -a /etc/apt/sources.list && sudo aptitude update && sudo aptitude install -y

```

---

### Post by longtom on 2009-03-08
> **sanus|art said:**
> Weird? Maybe this:
```

echo "deb http://www.remastersys.klikit-linux.com/repository remastersys/"  |  sudo tee -a /etc/apt/sources.list && sudo aptitude update && sudo aptitude install -y

```

Nope...  but thanks for the suggestion

longtom

---

### Post by longtom on 2009-03-08
Here the output:

```

 echo "deb http://www.remastersys.klikit-linux.com/repository remastersys/"  |  sudo tee -a /etc/apt/sources.list && sudo aptitude update && sudo aptitude install -y
deb http://www.remastersys.klikit-linux.com/repository remastersys/
Hit http://ppa.launchpad.net intrepid Release.gpg                               
Hit http://bw.archive.ubuntu.com intrepid Release.gpg                
Ign http://bw.archive.ubuntu.com intrepid/main Translation-en_ZA     
Ign http://bw.archive.ubuntu.com intrepid/restricted Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid/universe Translation-en_ZA 
Ign http://bw.archive.ubuntu.com intrepid/multiverse Translation-en_ZA
Hit http://bw.archive.ubuntu.com intrepid-security Release.gpg       
Ign http://bw.archive.ubuntu.com intrepid-security/main Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-security/restricted Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-security/universe Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-security/multiverse Translation-en_ZA
Hit http://bw.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://bw.archive.ubuntu.com intrepid-updates/main Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-updates/restricted Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-updates/universe Translation-en_ZA
Ign http://bw.archive.ubuntu.com intrepid-updates/multiverse Translation-en_ZA
Hit http://bw.archive.ubuntu.com intrepid Release                    
Hit http://bw.archive.ubuntu.com intrepid-security Release           
Hit http://bw.archive.ubuntu.com intrepid-updates Release                       
Hit http://bw.archive.ubuntu.com intrepid/main Packages              
Hit http://bw.archive.ubuntu.com intrepid/restricted Packages        
Hit http://bw.archive.ubuntu.com intrepid/universe Packages
Hit http://bw.archive.ubuntu.com intrepid/multiverse Packages        
Hit http://bw.archive.ubuntu.com intrepid/main Sources               
Hit http://bw.archive.ubuntu.com intrepid/restricted Sources
Hit http://bw.archive.ubuntu.com intrepid/universe Sources
Hit http://bw.archive.ubuntu.com intrepid/multiverse Sources
Hit http://bw.archive.ubuntu.com intrepid-security/main Packages     
Hit http://bw.archive.ubuntu.com intrepid-security/restricted Packages
Hit http://bw.archive.ubuntu.com intrepid-security/universe Packages 
Ign http://www.remastersys.klikit-linux.com remastersys/ Release.gpg
Hit http://bw.archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://bw.archive.ubuntu.com intrepid-security/main Sources      
Hit http://bw.archive.ubuntu.com intrepid-security/restricted Sources
Hit http://bw.archive.ubuntu.com intrepid-security/universe Sources
Hit http://bw.archive.ubuntu.com intrepid-security/multiverse Sources
Hit http://bw.archive.ubuntu.com intrepid-updates/main Packages
Hit http://bw.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://bw.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://bw.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://bw.archive.ubuntu.com intrepid-updates/main Sources
Hit http://bw.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://bw.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://bw.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://ppa.launchpad.net intrepid/main Translation-en_ZA
Hit http://ppa.launchpad.net intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid/main Translation-en_ZA
Hit http://ppa.launchpad.net intrepid Release  
Hit http://ppa.launchpad.net intrepid Release  
Ign http://www.remastersys.klikit-linux.com remastersys/ Translation-en_ZA
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://www.remastersys.klikit-linux.com remastersys/ Release
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Ign http://www.remastersys.klikit-linux.com remastersys/ Packages
Hit http://www.remastersys.klikit-linux.com remastersys/ Packages
Reading package lists... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

longtom

---

### Post by zvacet on 2009-03-08
System>admin<software sources and change server to** main**.

---

### Post by longtom on 2009-03-08
> **zvacet said:**
> System>admin<software sources and change server to** main**.

No joy.

```
Hit http://www.remastersys.klikit-linux.com remastersys/ Packages
Reading package lists... Done

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by ugm6hr on 2009-03-08
Provided that the "mother" PC and all others run the same version of Ubuntu (e.g. Gnome Ubuntu 8.10 32-bit), the simplest method is just to copy /var/cache/apt/archives (exc lock file) from the mother PC to others.

Then try again.

If the CD/DVD does not contain all dependencies, it won't work.  This may be because you didn't select all dependencies when writing the DVD, or because you are starting with different default installations.

Any CD with necessary .debs can be added as a source: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

---

### Post by longtom on 2009-03-08
> **ugm6hr said:**
> 
Any CD with necessary .debs can be added as a source: [https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

I do that - still there are always some lib files missing....

The size of the /var/cache/apt/ appears to be pretty much the same as the cd...but I'll give it a go anyway.

In the meantime I have downloaded the lib files seperately...which is not possible out there in the bundus, I'm afraid...

I'm sure there is a solution - we just need to find it.

Greetings

longtom

---

### Post by ugm6hr on 2009-03-08
> **longtom said:**
> In the meantime I have downloaded the lib files seperately...which is not possible out there in the bundus, I'm afraid..

You can download whatever you want:

```
sudo apt-get install -d blender
```

This should download blender and all dependencies to /var/cache/apt/archives

---

### Post by longtom on 2009-03-08
> **ugm6hr said:**
> You can download whatever you want:

```
sudo apt-get install -d blender
```

This should download blender and all dependencies to /var/cache/apt/archives

When I did that now it said, I have it all.  I'll check tonight.

Thank you

longtom

---

