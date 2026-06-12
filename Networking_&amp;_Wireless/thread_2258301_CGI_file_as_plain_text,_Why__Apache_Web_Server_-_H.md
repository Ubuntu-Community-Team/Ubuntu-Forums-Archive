---
title: "CGI file as plain text, Why? / Apache Web Server - How?"
date: 2014-12-26
forum: Networking &amp; Wireless
---

### Post by DiogoSaraiva on 2014-12-26
Hi,
I tryed to install a web server (DX spider) view here:
[http://www.dxcluster.org/main/adminmanual_en-7.html](http://www.dxcluster.org/main/adminmanual_en-7.html)

But when I open 192.168.1.104/cgi-bin/spider.cgi
Its show as plain text instead a Web Applet...
I tried Turn On CGI files "recognition", and then I had to 
copy the CGI file located at "/var/www/html/cgi-bin" to other folder in the system named "CGI-BIN" too...
But then the issue:

I have other folder in var/www/html named "client" that is the base to run spider.cgi
When I turned On CGI files recognition, I can't browser my "client" folder in 192.168.1.104 more again....

Why?

My question:
The Document Root was changed too???
where is now?

Other information:
I had too reinstall my Ubuntu and I don't remember how I do these things (how turn on cgi file recognition, etc..)...
Or if exists a better way can you tell me please, how I do It?

If you know can you please tell me how redirect eg:
example.no-ip.org or other no-ip free address to my web server?

Thank you very very much and have a nice day and a great new year...

---

### Post by Lars Noodén on 2014-12-26
What do you have in your configuration file for that virtual host?  The server needs to know to run files found in the cgi-bin directory.

---

### Post by DiogoSaraiva on 2014-12-26
What is the configuration file??

is this?

spider.cgi :
```

#!/usr/bin/perl


# cluster-web.pl - perl login script for cluster web interface.
# @author Ian Norton 
# - Based on clx-web by DL6DBH (ftp://clx.muc.de/pub/clx/clx-java_10130001.tgz)
# - Modified by PA4AB
# @version 0.2 beta.  20020519.


# Work out the hostname of this server.
use Sys::Hostname;
my $HOSTNAME = hostname();


# Please note that the HOSTNAME MUST be resolvable from the user end. Otherwise the
# web interface will NOT work.
# Uncomment and set the hostname manually here if the above fails.
# $HOSTNAME = "cr7akg.ddns.net" ;
$PORT = "7300" ;
$NODECALL = "CR7AKG" ;


# Send text/html header to the browser.
print "Content-type: text/html\n\n";


# Get the parameters passed to the script.
read (STDIN, $post_data, $ENV{CONTENT_LENGTH});


$callstart = index($post_data, "=") + 1 ;
$callend = index($post_data, "&") ;


$call = substr($post_data, $callstart, $callend - $callstart), 
$password = substr($post_data, index($post_data, "=", $callend) + 1, length($post_data)) ;


# Print the page header.
#print("Callsign : $call") ;
#print("Password : $password") ;
print <<'EOF';


<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0//EN">
<HTML LANG="EN">
    <HEAD>
        <TITLE>Cluster Web - DX Cluster Web Interface.</TITLE>
        <META HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1">
        <META NAME="Author" CONTENT="Ian Norton.">
        <META NAME="DESCRIPTION" CONTENT="DX Cluster web interface">
    </HEAD>
     
<BODY BGCOLOR="#FFFFFF" LINK="#008080" ALINK="#000099" VLINK="#000099">         


    <H1>
    <CENTER>
        <FONT FACE="arial, helvicta" COLOR="#008080" SIZE=+2>
        <B><BR>Cluster Web - DX Cluster Web Interface.</B><BR>
EOF


        print("Welcome to $NODECALL<BR>") ;


print <<'EOF';
        </FONT>
    </CENTER>
    </H1>


<BR CLEAR="ALL">


<HR>
EOF


if($ENV{CONTENT_LENGTH} > 0)
    {
    # Callsign is set - print the whole <APPLET> stuff....
    # print("Callsign is $call<BR>\n") ;


    print("<CENTER>\n") ;
    print("    <APPLET CODE=\"spiderclient.class\" CODEBASE=\"/client/\" width=800 height=130>\n") ;
    print("        <PARAM NAME=\"CALL\" VALUE=\"$call\">\n") ;
    print("        <PARAM NAME=\"PASSWORD\" VALUE=\"$password\">\n") ;
    print("        <PARAM NAME=\"HOSTNAME\" VALUE=\"$HOSTNAME\">\n") ;
    print("        <PARAM NAME=\"PORT\" VALUE=\"$PORT\">\n") ;
    print("        <PARAM NAME=\"NODECALL\" VALUE=\"$NODECALL\">\n") ;
    print("    </APPLET>\n") ;
    print("</CENTER>\n") ;
    }
else
    {
    # Callsign isn't set - print the login page.
    print <<'EOF';
    <CENTER>
    <FORM METHOD=POST>
        <STRONG>Please enter your callsign: </STRONG><BR>
        <INPUT name="call" size=10><BR>
        <STRONG>Please enter your password: </STRONG><BR>
        <INPUT name="password" size=10 TYPE=PASSWORD><BR>
        <INPUT type=submit value="Click here to Login">
    </FORM>
    <BR>If you do not have a password set - don't enter one :)
    </CENTER>
EOF
    }


print <<'EOF';
<HR>


<ADDRESS>
<A HREF="http://www.dxcluster.org/">Spider Homepage</A>.
</HTML>


EOF

```

---

### Post by Lars Noodén on 2014-12-26
Ok, that's the script.  If you have not modified anything from the default in /etc/apache2/sites-enabled/000-default.conf you will find your configuration for the main virtual host (for 14.04 LTS).

---

### Post by DiogoSaraiva on 2014-12-26
What should I do what that file?

uncoment this line: [FONT=Menlo] #Include conf-available/serve-cgi-bin.conf    
??

Thanks

file:
[/FONT]
```
[FONT=Menlo]<VirtualHost *:80>[/FONT]
[FONT=Menlo]        # The ServerName directive sets the request scheme, hostname and port that[/FONT]
[FONT=Menlo]        # the server uses to identify itself. This is used when creating[/FONT]
[FONT=Menlo]        # redirection URLs. In the context of virtual hosts, the ServerName[/FONT]
[FONT=Menlo]        # specifies what hostname must appear in the request's Host: header to[/FONT]
[FONT=Menlo]        # match this virtual host. For the default virtual host (this file) this[/FONT]
[FONT=Menlo]        # value is not decisive as it is used as a last resort host regardless.[/FONT]
[FONT=Menlo]        # However, you must set it for any further virtual host explicitly.[/FONT]
[FONT=Menlo]        #ServerName www.example.com[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]        ServerAdmin webmaster@localhost[/FONT]
[FONT=Menlo]        DocumentRoot /var/www/html[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,[/FONT]
[FONT=Menlo]        # error, crit, alert, emerg.[/FONT]
[FONT=Menlo]        # It is also possible to configure the loglevel for particular[/FONT]
[FONT=Menlo]        # modules, e.g.[/FONT]
[FONT=Menlo]        #LogLevel info ssl:warn[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]        ErrorLog ${APACHE_LOG_DIR}/error.log[/FONT]
[FONT=Menlo]        CustomLog ${APACHE_LOG_DIR}/access.log combined[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]        # For most configuration files from conf-available/, which are[/FONT]
[FONT=Menlo]        # enabled or disabled at a global level, it is possible to[/FONT]
[FONT=Menlo]        # include a line for only one particular virtual host. For example the[/FONT]
[FONT=Menlo]        # following line enables the CGI configuration for this host only[/FONT]
[FONT=Menlo]        # after it has been globally disabled with "a2disconf".[/FONT]
[FONT=Menlo]        #Include conf-available/serve-cgi-bin.conf[/FONT]
[FONT=Menlo]</VirtualHost>[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# vim: syntax=apache ts=4 sw=4 sts=4 sr noet[/FONT]

```

---

### Post by Lars Noodén on 2014-12-27
> **DiogoSaraiva said:**
> What should I do what that file?


I would just add a [ScriptAlias](http://httpd.apache.org/docs/2.4/mod/mod_alias.html#scriptalias) directive for the directory where you have your CGI script.  If you have /var/www/cgi-bin/ then you could add something like this for that virtual host:

```

        ScriptAlias /cgi-bin/ /var/www/cgi-bin/

```

That would make your script (e.g. foo.pl) available in [http://yoursite.example.org/cgi-bin/foo.pl](http://yoursite.example.org/cgi-bin/foo.pl)

Then just make sure that your perl script is executable and will run.  If you are using perl scripts that get called frequently with heavy use, then you might also look at using the [mod_perl](http://perl.apache.org/) module.

---

### Post by DiogoSaraiva on 2014-12-27
But how I can use "/var/www/html/cgi-bin" instead of "/usr/lib/cgi-bin" for my cgi scripts?

I already tried some things

I Activate cgi with the commands:

```

sudo chmod 755 /usr/lib/cgi-bin
sudo chown root.root /usr/lib/cgi-bin
sudo a2enmod cgi
sudo service apache2 restart

```

and placed a script called cgi-handler in "/usr/lib/cgi-bin" but when i go to 192.168.1.104/cgi-bin/cgi-handler.pl gives me this error:
```

**Internal Server Error**


[COLOR=#000000][FONT=Times]The server encountered an internal error or misconfiguration and was unable to complete your request.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]Please contact the server administrator at webmaster@localhost to inform them of the time this error occurred, and the actions you performed just before this error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Times]More information about this error may be available in the server error log.[/FONT][/COLOR]
[HR][/HR]Apache/2.4.7 (Ubuntu) Server at 192.168.1.104 Port 80
```

Can you help me please please.
Thank you very much...

---

### Post by Lars Noodén on 2014-12-28
> **DiogoSaraiva said:**
> But how I can use "/var/www/[s]html/[/s]cgi-bin" instead of "/usr/lib/cgi-bin" for my cgi scripts?

To do that you would make the directory and then use the [ScriptAlias](http://httpd.apache.org/docs/2.4/mod/mod_alias.html#scriptalias) directive inside your Apache2 configuration file for that virtual host.  

Diagnosing errors can be a little tricky.  One useful method is to open an extra terminal window and track the output of the error log to see what in the script is causing an error.  In the extra terminal window:

```

tail -f /var/log/apache2/error.log

```

and leave that running.  As you access the web server and produce errors, the error messages will show up live.  

An advanced option if you are using perl, but not one for production use only testing, would be to use the CGI::Carp module in your script.  That will trap errors and send a copy of the output to the browser as well as the logs.

```

use CGI::Carp 'fatalsToBrowser';

```

However, it's something that should be removed before putting the script into production.

---

### Post by DiogoSaraiva on 2014-12-28
Should I use /var/www/cgi-bin/ instead of /var/www/html/cgi-bin/
my java files are located in /var/www/html/client/

So, I will try this:

Write on top of apache2.conf this:

```

ScriptAlias /cgi-bin/ /var/www/html/cgi-bin/
<Directory /var/www/html/cgi-bin >
    SetHandler cgi-script
    Options ExecCGI
</Directory>

```

is this ok??

Thanks

---

### Post by Lars Noodén on 2014-12-28
The configuration looks about right but I would move /var/www/html/cgi-bin/ to /var/www/cgi-bin/ because /var/www/html/ is published by the web server and you generally do not want scripts available like that.  

Apache2 is designed so that you could have multiple web sites served from the same machine, but each with a separate, unique configuration.  So instead of apache2.conf, the better place would be /etc/apache2/sites-enabled/000-default.conf which is where Ubuntu gives a default virtual host.

---

### Post by DiogoSaraiva on 2014-12-28
figured out that no need to be in /var/www/html/cgi-bin/ for spider.cgi accessing /var/www/html/client folder (where are the java files...)
So... Sorry for that....
But can you please explain me how can I access my server 192.168.1.104/cgi-bin/spider.cgi for example, from the exterior, example with a no-ip domain?
example from [www.example.no-ip.org](www.example.no-ip.org)

Thanks

---

### Post by Lars Noodén on 2014-12-29
> **DiogoSaraiva said:**
> But can you please explain me how can I access my server 192.168.1.104/cgi-bin/spider.cgi for example, from the exterior, example with a no-ip domain?
example from [www.example.no-ip.org](www.example.no-ip.org)

First set up port forwarding in your router so that ports 80 and 443 go to 192.168.1.104.  The menus, of course, vary from model to model so you'll have to just look around in your router's admin interface to find what you need.  If you are using any kind of password for your scripts or other web interfaces, then you must set up and use HTTPS (port 443) for encryption.  It also might not hurt to ensure that your machine always gets the same IP address (192.168.1.104) each time, that too is in the router admin settings.  

Then for dynamic DNS, again, it depends on your router.  You need an account at No-IP or a similar service first.  Then, depending on the model of your router, you'll have a menu where you can enter dynamic DNS information so it can log in automatically.

---

### Post by DiogoSaraiva on 2014-12-29
Ok, thank you very much...

---

