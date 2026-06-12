---
title: "Need help with opensim"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by k33bz on 2009-10-02
I downloaded the opensim file through the repositories following these instructions [http://opensimulator.org/wiki/UnofficialDebPackages]("http://opensimulator.org/wiki/UnofficialDebPackages")

```
Which places the install files at /usr/lib/opensim
```

After that I tried these instructions which is in the read me file:
```
From the distribution type:
 * ./runprebuild.sh
 * nant
 * cd bin
 * mono ./OpenSim.exe 
```

However when I run ./runprebuild.sh I get
```
work@mobile:/usr/lib/opensim$ ./runprebuild.sh
bash: ./runprebuild.sh: No such file or directory
work@mobile:/usr/lib/opensim$ 

```

On a hunch that maybe it is already installed I went ahead and tried the rest of the steps yet I get no where.

```
work@mobile:/usr/lib/opensim$ nant
NAnt 0.85 (Build 0.85.2478.0; release; 10/14/2006)
Copyright (C) 2001-2006 Gerry Shaw
http://nant.sourceforge.net
work@mobile:/usr/lib/opensim$ cd bin
work@mobile:/usr/lib/opensim/bin$ mono ./OpenSim.exe
log4net:ERROR XmlHierarchyConfigurator: No appender named [NHibernateFileLog] could be found.
log4net:ERROR XmlHierarchyConfigurator: Appender named [NHibernateFileLog] not found.
log4net:ERROR [FileAppender] Unable to acquire lock on file /var/log/opensim/OpenSim.log. Access to the path "/var/log/opensim/OpenSim.log" is denied.
20:29:15 - [OPENSIM MAIN]: configured log4net using default OpenSim.exe.config
20:29:15 - Performing compatibility checks... 
20:29:15 - Environment is compatible.

20:29:15 - [CONFIG] Reading configuration settings
20:29:15 - [CONFIG] Could not load any configuration
20:29:15 - [CONFIG] Did you copy the OpenSim.ini.example file to OpenSim.ini?
work@mobile:/usr/lib/opensim/bin$ 



BUILD FAILED

Could not find a '*.build' file in '/usr/lib/opensim'

For more information regarding the cause of the build failure, run the build again in debug mode.

Try 'nant -help' for more information
work@mobile:/usr/lib/opensim$ 
```

I looked around for other ways to install it, however there was only one other way I have found. I cant even get it started though. After making sure I have everything installed and try to get the package through svn I get:
```
work@mobile:~$ svn co http://opensimulator.org/svn/opensim/trunk opensim
svn: Could not open the requested SVN filesystem
work@mobile:~$ 
```

I really could use the help.

Thanks

---

### Post by boblemur on 2009-10-02
ok you could try running:

```
runprebuild.sh
```

to find the file or you can run(this one might take a little longer):

```
find /home /usr /etc | grep runprebuild.sh
```

either one will give you the output like...

```
/path/to/file/called/runprebuild.sh
```

then use:
```
cd /path/to/file/called/
chmod +x runprebuild.sh
./runprebuild.sh

```

hope that helps u get over what your stuck on :)

---

### Post by k33bz on 2009-10-02
> **boblemur said:**
> ok you could try running:

```
runprebuild.sh
```

This came back as not recognizing the command. 

> **boblemur said:**
> to find the file or you can run(this one might take a little longer):

```
find /home /usr /etc | grep runprebuild.sh
```

either one will give you the output like...

```
/path/to/file/called/runprebuild.sh
```



And this brought up alot of different applications with that command, however none of them to do with opensim.

Unfortunately I am still stuck.

---

### Post by boblemur on 2009-10-02
sorry the first one is a typo.

should be:

```
locate runprebuild.sh
```

and for the second one could you please post the output of:

```
find /home /usr /etc 2> /dev/null | grep runprebuild.sh
```

because on my system that command gives no results if you are getting results then it must be finding something and id say its probably not a coincidence that you have those files and i dont.

so let me know what it gives you also you could try:

```
find /home /usr /etc 2> /dev/null | grep OpenSim.exe
```

posting both would help if you can :)

---

### Post by k33bz on 2009-10-03
Well now we are on the right track, at least I hope.

```
work@mobile:/usr/lib/opensim$ find /home /usr /etc 2> /dev/null | grep runprebuild.sh
/usr/lib/opensim/OpenSim/Tools/LaunchSLClient/runprebuild.sh

```

```
work@mobile:/usr/lib/opensim$ find /home /usr /etc 2> /dev/null | grep OpenSim.exe
/usr/lib/opensim/bin/OpenSim.exe
/usr/lib/opensim/bin/OpenSim.exe.config.orig
/usr/lib/opensim/bin/OpenSim.exe.mdb
/usr/lib/opensim/bin/OpenSim.exe.config
/usr/lib/opensim/OpenSim/Region/Application/bin/Debug/OpenSim.exe
/usr/lib/opensim/OpenSim/Region/Application/bin/Debug/OpenSim.exe.mdb
work@mobile:/usr/lib/opensim$ 

```

Still cant nant anything though, not even with sudo nant.

---

### Post by k33bz on 2009-10-03
ok, I have this all working, now I just need to know how to work with it. I have it configured, and everything is working with cli. How do I get a gui of the opensim?

---

