---
title: "MySQL Installation from RPM"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by jaya28inside on 2010-06-18
greetings everyone!
I have found that the way to install software via offline mode is
really takes time of course. I agree with that. And I'm still in the installation process, tough. 
Well, I hope this story telling could be easy to understand for all readers.

My Objective is to install mySQL server under this Ubuntu.
I go to mySQL webpage, and download the RPM file there.
And then I search around and get the story 

> 
"to install RPM in Debian Family You need to use Alien."


At the first, I have alien installed under my Ubuntu.
It was Alien v.879 and so I try to execute 

> 
sudo alien -iv MySQL-server-5.1.48-1.glibc23.i386.rpm

 
well, guess what??
I got problem saying that it failed chowning...something like 
that.

OK let it be.
I search through google.
And I found Alien version below 8.81 could not deal 
with GHOST file under RPM installation in DEBIAN family.

Well, so I  did searching and getting the Alien v.8.81 compiled in a Tar file.
I extract it successful.
And then execute

> 
./alien.pl


OK it has a feedback! So alien could be used without installation. I thought it was lucky.
THen i put the RPM file within the same folder of alien (current).
and then I execute;

> 
sudo ./alien.pl -iv MySQL-server-5.1.48-1.glibc23.i386.rpm


and guess what??
I got this last line which is confusing me.

> 
LANG=C rpm -qp --queryformat %{NAME} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{VERSION} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{ARCH} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{PREUN} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{LICENSE} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qp --queryformat %{PREIN} /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qcp /MySQL-server-5.1.48-1.glibc23.i386.rpm
	rpm -qpi /MySQL-server-5.1.48-1.glibc23.i386.rpm
	LANG=C rpm -qpl /MySQL-server-5.1.48-1.glibc23.i386.rpm
Warning: Skipping conversion of scripts in package MySQL-server: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.
	mkdir MySQL-server-5.1.48
mkdir: cannot create directory `MySQL-server-5.1.48': File exists
unable to mkdir MySQL-server-5.1.48:  at Alien/Package.pm line 257. 


well? I thought the current alien version which i am using is the stable one. And can get rid of mySQL error installation procedure.

Because I found out that...

> 
the older version alien (< v8.81) will not successfully handle the GHOST file under RPM installation procedure under DEBIAN family.


hmmm... 
the last error was mkdir error.
so then... ?

---

### Post by cariboo on 2010-06-18
Why not use the debs in the repositories? Just go to System->Administration->Synaptic Package Manager, or you can use the Software Center. Synaptic gives you the option to download the files for installation later. If you can only access the internet from Windows., go [here]("http://packages.ubuntu.com/"), and download the packages and dependencies needed.

---

### Post by jaya28inside on 2010-06-19
well, friends. I know i prefer not to choose Internet installation.
If i know i would. But, i try to do it manual. It's offline way.

Anyway,
I have done install it via Alien...

but somehow
I need to ensure whether it runs correctly or not.
Then i decided to restart it.

I try to check whether it runs on my ubuntu via this

> 
ps -ef|grep mysql


and i found the mysql is running, look at this feedback from the previous command,

> 
1000      3821  3803  0 00:20 pts/2    00:00:00 grep --color=auto mysql


But, somehow... once I figured it already run...
then i want to use this command 

> 
mysql stop


but, it generate this error

> 

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


well...

what's that?
i thought it was running already.

then, decided
to check it throught Synaptic Package Manager

and I found, it said it was installed already!

look,
[[IMG]http://img249.imageshack.us/img249/2120/screenshotoo.png[/IMG]](http://img249.imageshack.us/i/screenshotoo.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

So then,
now... 

i couldn't connect through it,
it always said, error socket!

why eh?

---

