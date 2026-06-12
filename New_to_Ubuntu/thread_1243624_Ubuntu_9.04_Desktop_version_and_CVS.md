---
title: "Ubuntu 9.04 Desktop version and CVS"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by sreddy64 on 2009-08-18
Does Ubuntu 9.04 Desktop version comes with CVS?. If not, how can I get compatible source/binary for CVS?. 
 
Thanks for your time.

---

### Post by jrothwell97 on 2009-08-18
CVS can be installed with the following command at the terminal:

```
sudo apt-get install cvs
```

You'll be asked to enter your password, and then confirm the installation. However, as I can see from your thread on the Installation forum, you can't do this as the machine is not connected to the Internet. I'd suggest looking at [Keryx](http://keryxproject.org/).

Good luck!

---

### Post by sreddy64 on 2009-08-18
Thanks for your posting. I was able to use Keryx package and download the updates.
When run the command
 
sudo dpkg -i –force-depends *.deb 
 
it is throwing lot of error messages like this and finally it exists. Am I doing anything wrong here?
 
Thanks
 
[COLOR=red]n of /usr/sbin/install-docs aborted due to compilation errors.[/COLOR]
[COLOR=red]dpkg: error processing dnsutils_9.5.1.dfsg.P2-1ubuntu0.1_i386.deb (--install):[/COLOR]
[COLOR=red]subprocess pre-removal script returned error exit status 9[/COLOR]
[COLOR=red]* Starting Common Unix Printing System: cupsd [ OK ] [/COLOR]
[COLOR=red]Preparing to replace ecryptfs-utils 73-0ubuntu6.1 (using ecryptfs-utils_73-0ubuntu6.1_i386.deb) ...[/COLOR]
[COLOR=red]Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.[/COLOR]
[COLOR=red]Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.[/COLOR]
[COLOR=red]Execution of /usr/sbin/install-docs aborted due to compilation errors.[/COLOR]
[COLOR=red]dpkg: error processing ecryptfs-utils_73-0ubuntu6.1_i386.deb (--install):[/COLOR]
[COLOR=red]subprocess pre-removal script returned error exit status 9[/COLOR]
[COLOR=red]* Starting Common Unix Printing System: cupsd [ OK ] [/COLOR]
[COLOR=red]Preparing to replace file 4.26-2ubuntu4 (using file_4.26-2ubuntu4_i386.deb) ...[/COLOR]
[COLOR=red]Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.[/COLOR]
[COLOR=red]Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.[/COLOR]
[COLOR=red]Execution of /usr/sbin/install-docs aborted due to compilation errors.[/COLOR]
[COLOR=red]dpkg: error processing file_4.26-2ubuntu4_i386.deb (--install):[/COLOR]
[COLOR=red]subprocess pre-removal script returned error exit status 9[/COLOR]
[COLOR=red] [/COLOR]

---

### Post by sreddy64 on 2009-08-19
Thank you very much for  pointing me to Keryx. I was able to update Ubuntu 9.04 using keryx , configure CVS and use it. Keryx is a nice utility if you are dealing with offline machines.

---

