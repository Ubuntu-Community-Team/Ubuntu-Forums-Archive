---
title: "Nathan bridgewater ASP.NET MVC2 &amp; 3 installation scripts"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by Drenriza on 2011-09-07
Hi guys.

Here recently i have experimented with some installation scripts and guides from nathan bridgewater, to get a ASP.NET server running.

The old install script but with the explanation for everything else.
[http://www.integratedwebsystems.com/2010/11/setting-up-mono-2-8-with-asp-net-4-0-and-mvc2-on-ubuntu-with-mysql-membership/](http://www.integratedwebsystems.com/2010/11/setting-up-mono-2-8-with-asp-net-4-0-and-mvc2-on-ubuntu-with-mysql-membership/)

New install script, but with no explanation. Look at link #1
[http://www.integratedwebsystems.com/2011/08/install-mono-2-10-3-on-ubuntu-using-bash-script/](http://www.integratedwebsystems.com/2011/08/install-mono-2-10-3-on-ubuntu-using-bash-script/)

And was wondering if anyone here have used them? The reason i ask is that i have some small problems. I have followed the guide but, at one part of the guide their are made some changes to a file, but their is no info (from what i can see) on what file it is the changes are made to :KS

> 
For this sample, we used all the default parameters in our configuration. Take note that debugging is enabled. I also left IO Mapping enabled to allow Mono to treat file system paths as case insensitive. You can improve performance by disabling IO Mapping. The VirtualHost configuration looks like this:

<VirtualHost *:80>
ServerName ubuntu
ServerAdmin web-admin@ubuntu
DocumentRoot /srv/www/ubuntu
# MonoServerPath can be changed to specify which version of ASP.NET is hosted
# mod-mono-server1 = ASP.NET 1.1 / mod-mono-server2 = ASP.NET 2.0
# For SUSE Linux Enterprise Mono Extension, uncomment the line below:
# MonoServerPath ubuntu "/opt/novell/mono/bin/mod-mono-server2"
# For Mono on openSUSE, uncomment the line below instead:
MonoServerPath ubuntu "/opt/mono-2.8/bin/mod-mono-server4"
 
# To obtain line numbers in stack traces you need to do two things:
# 1) Enable Debug code generation in your page by using the Debug="true"
#    page directive, or by setting <compilation debug="true" /> in the
#    application's Web.config
# 2) Uncomment the MonoDebug true directive below to enable mod_mono debugging
MonoDebug ubuntu true
 
# The MONO_IOMAP environment variable can be configured to provide platform abstraction
# for file access in Linux.  Valid values for MONO_IOMAP are:
#    case
#    drive
#    all
# Uncomment the line below to alter file access behavior for the configured application
MonoSetEnv ubuntu MONO_IOMAP=all;LD_LIBRARY_PATH=/opt/mono-2.8/lib:$LD_LIBRARY_PATH;PATH=/opt/mono-2.8/bin:$PATH
#
# Additional environtment variables can be set for this server instance using
# the MonoSetEnv directive.  MonoSetEnv takes a string of 'name=value' pairs
# separated by semicolons.  For instance, to enable platform abstraction *and*
# use Mono's old regular expression interpreter (which is slower, but has a
# shorter setup time), uncomment the line below instead:
# MonoSetEnv ubuntu MONO_IOMAP=all;MONO_OLD_RX=1
 
MonoApplications ubuntu "/:/srv/www/ubuntu"
<Location "/">
Allow from all
Order allow,deny
MonoSetServerAlias ubuntu
SetHandler mono
SetOutputFilter DEFLATE
SetEnvIfNoCase Request_URI "\.(?:gif|jpe?g|png)$" no-gzip dont-vary
</Location>
<IfModule mod_deflate.c>
AddOutputFilterByType DEFLATE text/html text/plain text/xml text/javascript
</IfModule>
</VirtualHost>

Also, my index.aspx is not read from /srv/www/ubuntu/ as where the guide says i should place my files, and i get an error (see picture) if i place the files in /var/www/

So if anyone have used his guides and got a working environment i would LOVE if you would give a little feedback on my issues.

Also if you know the following.
The guide is for ASP.NET MVC2 or 3, i ofc did not see this. And are wondering if this can display normal ASP.NET webpages.

Also, my system i have installed this on is not a virtual environment.

Thanks on advance.
Kind regards.

---

