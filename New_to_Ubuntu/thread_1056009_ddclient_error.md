---
title: "ddclient error"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by spikoley on 2009-01-31
I am trying to get ddclient working with eNom.  The eNom patch is applied and I have triple checked and changed the password.  I keep on receiving the error below.  Any ideas?

```
# /etc/ddclient.conf
login=mydomain.net
protocol=enom
password=mypassword
use=web
domain=mydomain.net
server=dynamic.name-services.com. protocol=enom www
```

> WARNING:  file /etc/ddclient.conf, line 6: Invalid Value for keyword 'protocol' = 'enom'
WARNING:  file /etc/ddclient.conf, line 9: unrecognized keyword 'domain' (ignored)
WARNING:  file /etc/ddclient.conf, line 10: Invalid Value for keyword 'protocol' = 'enom'
WARNING:  file /etc/ddclient.conf, line 6: Invalid Value for keyword 'protocol' = 'enom'
WARNING:  file /etc/ddclient.conf, line 9: unrecognized keyword 'domain' (ignored)
WARNING:  file /etc/ddclient.conf, line 10: Invalid Value for keyword 'protocol' = 'enom'
CONNECT:  checkip.dyndns.org
CONNECTED:  using HTTP
SENDING:  GET / HTTP/1.0
SENDING:   Host: checkip.dyndns.org
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 200 OK

RECEIVE:  Content-Type: text/html

RECEIVE:  Server: DynDNS-CheckIP/1.0

RECEIVE:  Connection: close

RECEIVE:  Cache-Control: no-cache

RECEIVE:  Pragma: no-cache

RECEIVE:  Content-Length: 105

RECEIVE:  

RECEIVE:  <html><head><title>Current IP Check</title></head><body>Current IP Address: my.ip.here</body></html>

INFO:     forcing update of www.
INFO:     setting IP address to my.ip.here for www
UPDATE:   updating www
CONNECT:  dynamic.name-services.com.
CONNECTED:  using HTTP
SENDING:  GET /nic/update?system=dyndns&hostname=www&myip=my.ip.here HTTP/1.0
SENDING:   Host: dynamic.name-services.com.
SENDING:   Authorization: Basic YXRub25lLm5ldDpwyXNzd29yzA==
SENDING:   User-Agent: ddclient/3.7.3
SENDING:   Connection: close
SENDING:   
RECEIVE:  HTTP/1.1 404 Not Found

RECEIVE:  Content-Length: 1635

RECEIVE:  Content-Type: text/html

RECEIVE:  Server: Microsoft-IIS/6.0

RECEIVE:  X-Powered-By: ASP.NET

RECEIVE:  Date: Sat, 31 Jan 2009 15:36:42 GMT

RECEIVE:  Connection: close

RECEIVE:  

RECEIVE:  <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

RECEIVE:  <HTML><HEAD><TITLE>The page cannot be found</TITLE>

RECEIVE:  <META HTTP-EQUIV="Content-Type" Content="text/html; charset=Windows-1252">

RECEIVE:  <STYLE type="text/css">

RECEIVE:    BODY { font: 8pt/12pt verdana }

RECEIVE:    H1 { font: 13pt/15pt verdana }

RECEIVE:    H2 { font: 8pt/12pt verdana }

RECEIVE:    A:link { color: red }

RECEIVE:    A:visited { color: maroon }

RECEIVE:  </STYLE>

RECEIVE:  </HEAD><BODY><TABLE width=500 border=0 cellspacing=10><TR><TD>

RECEIVE:  

RECEIVE:  <h1>The page cannot be found</h1>

RECEIVE:  The page you are looking for might have been removed, had its name changed, or is temporarily unavailable.

RECEIVE:  <hr>

RECEIVE:  <p>Please try the following:</p>

RECEIVE:  <ul>

RECEIVE:  <li>Make sure that the Web site address displayed in the address bar of your browser is spelled and formatted correctly.</li>

RECEIVE:  <li>If you reached this page by clicking a link, contact

RECEIVE:   the Web site administrator to alert them that the link is incorrectly formatted.

RECEIVE:  </li>

RECEIVE:  <li>Click the <a href="javascript:history.back(1)">Back</a> button to try another link.</li>

RECEIVE:  </ul>

RECEIVE:  <h2>HTTP Error 404 - File or directory not found.<br>Internet Information Services (IIS)</h2>

RECEIVE:  <hr>

RECEIVE:  <p>Technical Information (for support personnel)</p>

RECEIVE:  <ul>

RECEIVE:  <li>Go to <a href="http://go.microsoft.com/fwlink/?linkid=8180">Microsoft Product Support Services</a> and perform a title search for the words <b>HTTP</b> and <b>404</b>.</li>

RECEIVE:  <li>Open <b>IIS Help</b>, which is accessible in IIS Manager (inetmgr),

RECEIVE:   and search for topics titled <b>Web Site Setup</b>, <b>Common Administrative Tasks</b>, and <b>About Custom Error Messages</b>.</li>

RECEIVE:  </ul>

RECEIVE:  

RECEIVE:  </TD></TR></TABLE></BODY></HTML>


---

### Post by jbrown96 on 2009-01-31
I tried ddlcient for a while. I never had much success, and ended up using tomato on my router to get dyndns service. 

I think > ```
# /etc/ddclient.conf
login=mydomain.net
protocol=enom
password=mypassword
use=web
domain=mydomain.net
server=dynamic.name-services.com. protocol=enom www


```

I think that the first protocol part should be either http or https. Not sure though, and I couldn't find a configuration guide quickly through a search. Could you give a link to the instructions you used?

---

### Post by spikoley on 2009-02-01
> **jbrown96 said:**
> I tried ddlcient for a while. I never had much success, and ended up using tomato on my router to get dyndns service. 

I think 

I think that the first protocol part should be either http or https. Not sure though, and I couldn't find a configuration guide quickly through a search. Could you give a link to the instructions you used?

Here are the directions I used.

> Downloaded the patch from [https://sourceforge.net/tracker/index.php?func=detail&aid=1556605&group_id=116817&atid=676130](https://sourceforge.net/tracker/index.php?func=detail&aid=1556605&group_id=116817&atid=676130)  
 
Installed the program "patch" --> sudo apt-get install patch 
 
Then run the program patch to update your ddclient 
> patch < "downloaded file"  
 
You might get the question which file you want to patch --> /usr/sbin/ddclient 
 
Final step is to update you ddclient.conf file: 
 
# Configuration file for ddclient 
# /etc/ddclient.conf 
login=YourDomain 
protocol=enom 
password=YourPassword 
use=web 
domain=YourDomain 
server=dynamic.name-services.com. protocol=enom www 
 
To force the running and get proof for a working update type:  
 
> sudo ddclient -force -verbose|more 

---

