---
title: "Conky &amp; home network users"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by SaaTeeVaaGreen on 2009-06-01
hi. i wonder if anyone could help a beginner with a couple of lines of code for conky...

i would like to able to add to conkys config file a couple of lines of code that would let me see how many users are logged on to my router/network at home and, if possible the user names an ip addresses of them. does anyone know how to do this?? 

i thought it would be the user_number and user_names but these didnt seem to work, so any advice would be greatly appreciated!:D

---

### Post by _AndY on 2009-06-02
I don't think it's going to be that easy.
I'd say your best bet would be to write a script to go off to your router and extract the information (there's usually a page in the web interface showing connected clients).
Once that script does what you need you can run it using
```
${execi 600 myscript}
```
in your .conkyrc, where 600 is the update interval in seconds (10 minutes in this case).

Hope that helps,
Andy

---

### Post by SaaTeeVaaGreen on 2009-06-02
thanks for your response. unfortunately, still being something of a beginner, writing my own script is a little beyond me at the moment!

however, i do know that the web interface does contain a page showing this info, as you mention, so its a starting point. i shall go away and do some research and see if i can come up with something!

---

### Post by aktiwers on 2009-06-02
You have a link for that picture? :)

Are you sure its on the router/network and not just  on the local machine?

---

### Post by Celauran on 2009-06-02
> **SaaTeeVaaGreen said:**
> however, i do know that the web interface does contain a page showing this info, as you mention, so its a starting point. i shall go away and do some research and see if i can come up with something!

wget or Python's urllib sound like good places to start, then.

---

### Post by SaaTeeVaaGreen on 2009-06-02
> You have a link for that picture?

what, you mean my avatar? its a fine detail taken from a painting by a spanish artist called Miro.

> Are you sure its on the router/network and not just on the local machine?

im sorry, im not sure what you mean here. do you mean the web interface for the router? its accessible by all machines that are connected to the router and is like a gui for maintaining router settings *etc*. is that what you meant? (sorry, still learning about all this stuff!:confused:)

---

### Post by SaaTeeVaaGreen on 2009-06-02
> wget or Python's urllib sound like good places to start, then.

thanks Celauran, i will have a look at these

---

### Post by aktiwers on 2009-06-02
I ment the screenshot of the conky you talked about..  but nevermind :)

I have done a little Python scripting maybe I could help.. or..

I guess the script needs to wget the stats page from your router like ever 1min or whatever,
and print the content from there.

Edit: or actually I think Python and the urllib can do this alone

---

### Post by Celauran on 2009-06-02
> **aktiwers said:**
> Edit: or actually I think Python and the urllib can do this alone

It can. Use urllib2 to get the info from the page, then use a regex to filter out IPs. Shouldn't be too hard, really.

---

### Post by SaaTeeVaaGreen on 2009-06-02
thanks for the advice guys! i will certainly try this out.

probably a stupid question (and probably not my first!) but what it python? i take it i need to apt-get it, run it and go from there? and urllib2 & regex are part of python? or these need to be installed separately?

---

### Post by Celauran on 2009-06-02
Python is a programming language. I believe it is installed by default with Ubuntu. urllib2 is a Python library, and regex simply refers to regular expressions.

I threw this together in about eight seconds, so there will be mistakes, but this should at least get you started:

```
#!/usr/bin/env python

import re
import urllib2

router = "http://user:password@ipaddress/path"
regex = re.compile('[0-9]{1,3}(\.[0-9]{1,3}){3}')

url = urllib2.urlopen(router).read()
if regex.search(url) != None:
    print regex.search(url).group()
```

The documentation at [python.org](http://www.python.org) is great, though, so you shouldn't have much trouble getting a working script.

EDIT: router line will obviously need to be changed with appropriate information

---

### Post by Celauran on 2009-06-02
Alright, this is working fine on my D-Link router. May require a little tweaking depending on your router make/model.

```
#!/usr/bin/env python

import re
import urllib

username = removed
password = removed
routerURL = "192.168.0.1/h_dhcp.html"
protocol = "http://"

regex = re.compile('^\"[0-9]{1,3}\,.*?\,[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

ipList = []

for line in routerPage:
        if regex.search(line) != None:
                ipList.append(line.strip())

for ip in ipList:
        ip = ip.split(',')
        print ip[1], ip[2]
```

I'd start with getting just to routerPage and printing the output to see what the format's like. My router helpfully creates a JavaScript array right at the top of the page and my regex is built around that.

---

### Post by SaaTeeVaaGreen on 2009-06-03
Celauran, this is great, thanks very much.

although parts of your script are a little beyond me at the moment i will spend some time going through the python documentation and im sure i will get my head round it in the end! besides, im only to happy to learn. hell, thats why im here!:D

---

### Post by aktiwers on 2009-06-03
This should work perfectly fine for you SaaTeeVaagreen..

You could try it out.

First copy/paste the script into a text document, then edit the "username =" "your username" to fit what you use for your router. With the quotes.

And do that to the other fields as well..(password, routerURL).

Then save the text in your home folder as: check.py

Then open Terminal( Applications => Accessories => Terminal)

And type in:
```
python check.py
```Thats it. If I am being extremely obvious - sorry, you never know ;)

---

### Post by SaaTeeVaaGreen on 2009-06-08
aktiwers, thanks very much for your response, and not too obvious at all! also, sorry its taken a while for me to reply, have been away for a few days with no internet, no laptop and no ubuntu:(

anyway, im back now and have tried as you suggested, but im not sure its working. heres the output from python check.py:

```
me@my-laptop:~$ python check.py
Traceback (most recent call last):
  File "check.py", line 13, in <module>
    routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()
  File "/usr/lib/python2.6/urllib.py", line 87, in urlopen
    return opener.open(url)
  File "/usr/lib/python2.6/urllib.py", line 203, in open
    return getattr(self, name)(url)
  File "/usr/lib/python2.6/urllib.py", line 331, in open_http
    h = httplib.HTTP(host)
  File "/usr/lib/python2.6/httplib.py", line 984, in __init__
    self._setup(self._connection_class(host, port, strict))
  File "/usr/lib/python2.6/httplib.py", line 656, in __init__
    self._set_hostport(host, port)
  File "/usr/lib/python2.6/httplib.py", line 668, in _set_hostport
    raise InvalidURL("nonnumeric port: '%s'" % host[i+1:])
httplib.InvalidURL: nonnumeric port: ''
```

is this right? or can you see anything i may have done wrong? thanks very much.

---

### Post by Celauran on 2009-06-08
That's definitely not normal. Can you copy/paste the script from your machine? (blank out your username/password, of course)

---

### Post by aktiwers on 2009-06-08
Although the script does not work on my router, it runs fine. It's just that my router pages are in Java I guess, so it does not output the correct info, it actually just outputs nothing.
But it does run through without errors..  so..

I guess your mistake is in the routerURL line..  remember NOT to include the "http://" in that.. like mine looks like this:
```
routerURL = "[192.168.1.1/DHCPClientTable.htm]("http://192.168.1.1/DHCPClientTable.htm")"
```So no "http://" in the routerURL field, as its already included in the protocol = "http://" line.

---

### Post by SaaTeeVaaGreen on 2009-06-08
here it is

```
#!/usr/bin/env python

import re
import urllib

username = "***"
password = "***"
routerURL = "***"
protocol = "http://"

regex = re.compile('^\"[0-9]{1,3}\,.*?\,[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

ipList = []

for line in routerPage:
        if regex.search(line) != None:
                ipList.append(line.strip())

for ip in ipList:
        ip = ip.split(',')
        print ip[1], ip[2]
```

its basically exactly as you suggested, with username, password and router url added where i have put ***

---

### Post by Celauran on 2009-06-08
> **aktiwers said:**
> Although the script does not work on my router, it runs fine. It's just that my router pages are in Java I guess, so it does not output the correct info, it actually just outputs nothing.
But it does run through without errors..  so..


Well, the thing is I could obviously only test it with my own router. Your router's output is bound to be different, so the regular expression will need some tweaking. My router creates a JS array right at the top of the page in the form:

```
"connection number,hostname,IP"
```

and so my regular expression was built around this. I wasn't expecting the script to work 'out of the box' for everyone, but rather as a rough idea on how to approach the problem.

What seems to be happening in SaaTeeVaaGreen's case is that the user: password@domain (grr, stupid emotes) approach is being rejected. It worked fine for me using urllib in Python 2.5.2, but things may have changed some in Python 2.6.x. May want to look at urllib2 and how it handles authentication. Specifically, [this page](http://www.voidspace.org.uk/python/articles/authentication.shtml) may be of use.

---

### Post by SaaTeeVaaGreen on 2009-06-08
> remember NOT to include the "http://"

ok, i didnt remember that! i have now removed it from the script and run 'python check.py' again. now i get no output from that command in terminal at all.

is that better or worse??

---

### Post by aktiwers on 2009-06-08
That is better, because now the script runs without errors. Same as for me.
But I can't get it to output the right stuff. I think it might be in the regex part of the script, which I suck bad at, so I wont be able to help.

Celauran, I know it's not ment to work "out of the box". It's a great script, that made me start playing with Python again :) 

Can you confirm that it must be the reqex part we need to work on here?

---

### Post by Celauran on 2009-06-08
In all likelihood, that's what it is. Try modifying it like so:

```

#!/usr/bin/env python

import re
import urllib

username = "***"
password = "***"
routerURL = "***"
protocol = "http://"

regex = re.compile('^\"[0-9]{1,3}\,.*?\,[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

print routerPage

#ipList = []

#for line in routerPage:
#        if regex.search(line) != None:
#                ipList.append(line.strip())

#for ip in ipList:
#        ip = ip.split(',')
#        print ip[1], ip[2]
```

That should display the HTML output by the router, and then you can examine where and how the relevant information is being displayed. Once you've got that, coming up with a suitable regular expression shouldn't be difficult at all.

---

### Post by aktiwers on 2009-06-08
yeah now I get all the HTML, and I'm sure SaaTeeVaaGreen will do so too.

Now I better go read up on some regex, thanks :)

---

### Post by SaaTeeVaaGreen on 2009-06-08
i have commented out the lines you said and running python check.py is indeed printing the html output of the page. so this means the first part of the script is working correctly right?

ive some experience with html so im now going through it to identify whereabouts, and how, the info im after is being displayed. i may need some pointers on amending the regex part of the script however....

thanks so much for all your help so far Celauran and aktiwers

---

### Post by Celauran on 2009-06-08
Once you've isolated the HTML chunk containing the IP addresses and hostnames, I'll be happy to help you come up with a regular expression. After that, your script should be done.

---

### Post by aktiwers on 2009-06-08
Post your HTML for us to see then. I would love to see how Celauran uses regex on it :D

Here is mine:
> 
['<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">\r\n', '<html>\r\n', '<head>\r\n', '<title>DHCP Active IP Table</title>\r\n', '<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">\r\n', '\r\n', '\r\n', '<meta name="description" content="LINKSYS RVS4000 1001">\r\n', '<META http-equiv="Pragma" CONTENT="no-cache">\r\n', '<META HTTP-EQUIV="Cache-Control" CONTENT="no-cache">\r\n', '\r\n', '<LINK REL="stylesheet" TYPE="text/css" HREF="cisco.css">\r\n', '\r\n', '<script language="javascript" type="text/javascript" src="func.js"></script>\r\n', '<script language="javascript" type="text/javascript" src="msg.js"></script>\r\n', '<script language="javascript" type="text/javascript" src="linux.js"></script>\r\n', '<script language="javascript" type="text/javascript">\r\n', '<!-- hide script from old browsers\r\n', '\r\n', 'function deleteHost()\r\n', '{\t\r\n', '   \tvar cf = document.forms[0];\r\n', '\t\r\n', '\t//submit, todo set to "delete"\r\n', "\tcf.todo.value = 'delete';\r\n", '    cf.submit();\r\n', '}\r\n', '// \r\n', '//-->\t\r\n', '</script>\r\n', '</head>\r\n', '<body bgColor="#808080" onLoad="window.focus();">\r\n', '<form name="dhcpclientable" method="post" action="setup.cgi" onSubmit="return false">\r\n', '<div align="center">\r\n', '<table border="0" cellSpacing="0" cellPadding="0" width="660" bgColor="#ffffff">\r\n', '<tr>\r\n', '<td bgcolor="#6666cc">\r\n', '  <br><hr size="1" color="#ffffff"><img src="UI_Linksys.gif" width="164" height="57" alt="" border="0">\r\n', '  </TD>\r\n', '\r\n', '</TR>\r\n', '<tr>\r\n', '<td >\r\n', '<table border="0" cellspacing="0" cellpadding="4">\r\n', '<tr>\r\n', ' <td height="7" bgcolor="#E7E7E7" width="165"></TD>\r\n', ' <td height="7" width="533" colspan="2"></TD>\r\n', '\r\n', '</TR>\t\t\t\r\n', '\t\t\t    <tr>\r\n', ' <td width="164" height="24" align="right" class="bwhead" valign="top">DHCP Active IP Table</TD>\r\n', ' <td>&nbsp;</TD>\r\n', '\r\n', '</TR>\r\n', '\t\t\t    \r\n', '<tr>\r\n', ' <td bgColor="#e7e7e7">&nbsp; </TD>\r\n', '<td>\r\n', '<div class="indent8">\r\n', ' <table border="0" cellspacing="3" cellpadding="0" bgcolor="#ffffff" width="500">\r\n', '  <tr> \r\n', '   <td nowrap colspan="5"><B style="color:#0000ff; font-size:120%">DHCP Active IP Table</b></TD>\r\n', '  </TR>\r\n', '  <tr> \r\n', '   <td nowrap colspan="4">DHCP Server IP Address: &nbsp; 192.168.1.1</TD>\r\n', '   <td nowrap align="center" height="30">\r\n', '   <input type="button" name="refresh" value="Refresh" class="slbutton" onClick="location.href=\'DHCPClientTable.htm\'">\r\n', '   </TD>\r\n', '  </TR>\r\n', '  <tr bgColor="#b3b3b3">\r\n', '   <th nowrap height="30">Client Host Name</th>\r\n', '   <th nowrap>IP Address</th>\r\n', '   <th nowrap>MAC Address</th>\r\n', '   <th nowrap>Expires</th>\r\n', '   <th nowrap><input type="button" name="delete" value="Delete" onClick="deleteHost()"></th>\r\n', '  </TR>\r\n', '  <tr><td nowrap align="center" class="sub"><input type="hidden" name="name0" value="HAL2"><b>HAL2</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="ip0" value="192.168.1.100"><b>192.168.1.100</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="mac0" value="00:22:15:35:03:B4"><b>00:22:15:35:03:B4</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="expires0" value="71589"><b>71589</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="checkbox" name="del_box0" value="del_box0"></td>\r\n', '</tr>\r\n', '<tr><td nowrap align="center" class="sub"><input type="hidden" name="name1" value="EVILMAHMOOD"><b>EVILMAHMOOD</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="ip1" value="192.168.1.101"><b>192.168.1.101</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="mac1" value="00:0D:60:F0:9D:C7"><b>00:0D:60:F0:9D:C7</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="hidden" name="expires1" value="71589"><b>71589</b></td>\r\n', '<td nowrap align="center" class="sub"><input type="checkbox" name="del_box1" value="del_box1"></td>\r\n', '</tr>\r\n', '\r\n', '  \r\n', '\r\n', '<tr>\r\n', '<td nowrap colspan="4">&nbsp; </TD>\r\n', '<td nowrap align="center" height="30">\r\n', '<input type="button" name="close" value="Close" class="slbutton" onClick="self.close()"></TD>\r\n', '</TR>\r\n', '</table>\r\n', '    <br> &nbsp; \r\n', '\r\n', '</div>\r\n', '</TD>\r\n', '</TR></table>\r\n', '</TD>\r\n', '</TR></table>\r\n', '\r\n', '</div>\r\n', '\r\n', '\r\n', '<input type="hidden" name="h_d_0" value="">\r\n', '\r\n', '<input type="hidden" name="todo" value="none">\r\n', '<input type="hidden" name="this_file" value="DHCPClientTable.htm">\r\n', '<input type="hidden" name="next_file" value="DHCPClientTable.htm">\r\n', '<input type="hidden" name="message" value="">\r\n', '\t    \r\n', '</form>\r\n', '</body>\r\n', '</html>\r\n']


If you have time, I would love to get some help too.. my mind is having a hard time (again) getting the logic of [Regex]("http://docs.python.org/dev/howto/regex.html") or atleast how to use it.

---

### Post by SaaTeeVaaGreen on 2009-06-08
will post the relevant part of the html soon. sadly, im in work tomorrow and i gotta get some sleep now. although this is far more fun & interesting than anything i do in work, and i could stay up all night playing with this, im sure my boss would prefer me awake tomorrow rather than asleep at my desk all day!! if only i didnt have all those bills to pay, could forget about work and spend my whole life playing with ubuntu and all its associated joys!!

---

### Post by Celauran on 2009-06-08
> **aktiwers said:**
> If you have time, I would love to get some help too.. my mind is having a hard time (again) getting the logic of [Regex]("http://docs.python.org/dev/howto/regex.html") or atleast how to use it.

Not the most elegant thing on earth, but it works:

```
#!/usr/bin/env python

import re
import urllib

username = "username"
password = "password"
routerURL = "URL without http://"
protocol = "http://"

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

regex_name = re.compile('name=\"name.*?<\/b')
regex_ip = re.compile('<b>[0-9]{1,3}(\.[0-9]{1,3}){3}<\/b>')
regex_mac = re.compile('<b>[0-9A-F]{2}(:[0-9A-F]{2}){5}<\/b>')

routerName = []
routerIP = []
routerMAC = []

for line in routerPage:
    if regex_name.search(line) != None:
        routerName.append(str(re.findall('<b>.*?<\/b>', line)).replace('<b>', '').replace('</b>', '').replace('[', '').replace(']','').strip('\''))
    if regex_ip.search(line) != None:
        routerIP.append(str(regex_ip.search(line).group()).replace('<b>', '').replace('</b>', ''))
    if regex_mac.search(line) != None:
        routerMAC.append(str(regex_mac.search(line).group()).replace('<b>', '').replace('</b>', ''))

final = [['Hostname', 'IP Address', 'MAC Address']]
i = 0
while i < len(routerName):
    final.append([routerName[i], routerIP[i], routerMAC[i]])
    i += 1

for PC in final:
    print PC[0], PC[1], PC[2]
```

---

### Post by aktiwers on 2009-06-08
Wow thanks a lot! Now I understand why I could not figure it out.. this is way over my head! :D

But I fixed a small typo in your for loop. "for line in html" should be "for line in routerPage".

It works great!

I really need to learn this stuff..  been watching a video on youtube and I'm now reading up on the regex documentation on the python pages.. 

I also found this
[http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

Thanks a lot for your work mate, that sure gives some nice outputs :)

---

### Post by Celauran on 2009-06-08
> **aktiwers said:**
> But I fixed a small typo in your for loop. "for line in html" should be "for line in routerPage".
Good catch! I'd been working from a file containing your HTML output, so I used a different variable.

---

### Post by SaaTeeVaaGreen on 2009-06-09
hi, i posted my html output below

> <table class='edittable' width='100%' cellspacing='0' cellpadding='0' border='0'>\n", "<tr><td colspan='5' class='black'><img src='/images/spacer.gif' border='0' width='1' height='1' alt=''><br></td></tr>\n", "<tr><td colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><th align='left'>Name</th><th align='left'>IP Address</th><th align='left'>Interface</th><th colspan='2'></th></tr>\n", "<tr><td colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td colspan='5' class='black'><img src='/images/spacer.gif' border='0' width='1' height='1' alt=''><br></td></tr>\n", "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='oddrow'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/dexxacmd.gif' alt=' BT Home Hub' border='0'></td><td valign='middle'>api</td></tr></table>\n", "</td><td class='oddrow' align='left'>192.168.1.254</td><td class='oddrow' align='left'>&nbsp;</td><td class='oddrow' align='center' valign='middle'>&nbsp;</td><td class='oddrow' align='center' valign='middle'>&nbsp;</td></tr>\n", "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'evenrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=me&key=00:0a:e6:83:74:18\')"><img src=\'/images/ddesacmd.gif\' alt=\'Active Desktop\' border=\'0\'>me</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='evenrow' align='left'>192.168.1.66</td><td class='evenrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/ieth__md.gif' alt='Ethernet Interface' border='0'></td><td valign='middle'>ethport1</td></tr></table>\n", '</td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=me&key=00:0a:e6:83:74:18\')">Edit</a></td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:0a:e6:83:74:18\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'oddrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=mydesktop&key=00:0b:6a:63:26:ba\')"><img src=\'/images/ddesacmd.gif\' alt=\'Active Desktop\' border=\'0\'>mydesktop</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='oddrow' align='left'>192.168.1.67</td><td class='oddrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/ieth__md.gif' alt='Ethernet Interface' border='0'></td><td valign='middle'>ethport2</td></tr></table>\n", '</td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=mydesktop&key=00:0b:6a:63:26:ba\')">Edit</a></td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:0b:6a:63:26:ba\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'evenrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=mylaptop&key=00:12:f0:53:0a:5c\')"><img src=\'/images/ddesacmd.gif\' alt=\'Active Desktop\' border=\'0\'>mylaptop</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='evenrow' align='left'>192.168.1.65</td><td class='evenrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/iwla__md.gif' alt='WLAN Interface' border='0'></td><td valign='middle'>WLAN</td></tr></table>\n", '</td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=mylaptop&key=00:12:f0:53:0a:5c\')">Edit</a></td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:12:f0:53:0a:5c\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'oddrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=exlaptop&key=00:14:a5:66:90:d5\')"><img src=\'/images/ddesinmd.gif\' alt=\'Inactive Desktop\' border=\'0\'>exlaptop</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='oddrow' align='left'>192.168.1.68</td><td class='oddrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/iwla__md.gif' alt='WLAN Interface' border='0'></td><td valign='middle'>WLAN</td></tr></table>\n", '</td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=exlaptop&key=00:14:a5:66:90:d5\')">Edit</a></td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:14:a5:66:90:d5\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'evenrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=Joes-PC&key=00:16:17:dd:74:b2\')"><img src=\'/images/ddesinmd.gif\' alt=\'Inactive Desktop\' border=\'0\'>Joes-PC</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='evenrow' align='left'>192.168.1.68</td><td class='evenrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/ieth__md.gif' alt='Ethernet Interface' border='0'></td><td valign='middle'>unknown</td></tr></table>\n", '</td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=Joes-PC&key=00:16:17:dd:74:b2\')">Edit</a></td><td class=\'evenrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:16:17:dd:74:b2\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='evenrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", '<tr><td class=\'oddrow\'><table cellspacing=\'0\' cellpadding=\'0\' border=\'0\'><tr><td><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/ov/\', \'name=ex2laptop&key=00:16:44:e5:a5:2c\')"><img src=\'/images/ddesinmd.gif\' alt=\'Inactive Desktop\' border=\'0\'>ex2laptop</a></td><td valign=\'middle\'></td></tr></table>\n', "</td><td class='oddrow' align='left'>192.168.1.64</td><td class='oddrow' align='left'><table cellspacing='0' cellpadding='0' border='0'><tr><td><img src='/images/iwla__md.gif' alt='WLAN Interface' border='0'></td><td valign='middle'>WLAN</td></tr></table>\n", '</td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:GoAndRemember(\'/cgi/b/_dev_/cfg/\', \'name=ex2laptop&key=00:16:44:e5:a5:2c\')">Edit</a></td><td class=\'oddrow\' align=\'center\' valign=\'middle\'><a href="javascript:submitForm(document.device,22,0,\'00:16:44:e5:a5:2c\',\'\',0,\'\');">Delete</a></td></tr>\n', "<tr><td class='oddrow' colspan='5'><img src='/images/spacer.gif' border='0' width='1' height='3' alt=''><br></td></tr>\n", "<tr><td colspan='5' class='black'><img src='/images/spacer.gif' border='0' width='1' height='1' alt=''><br></td></tr>\n", '</table>

i havent included it all as the output was huge, i have just tried to include the section containing the information i am after (if you need it all to write the script let me know and i will post). the information (when displayed on page) is contained in a table which lists current active users, as well as all users that have connected to the router at any point (differentiated by Active Desktop & Inactive Desktop). i would just like to know the username and ip address of users currently online.
thanks so much for this

---

### Post by Celauran on 2009-06-09
Slight modification of aktiwers'

```
#!/usr/bin/env python

import re
import urllib

username = "username"
password = "password"
routerURL = "URL without http://"
protocol = "http://"

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

regex_name = re.compile('\/cfg\/\', \'name=.*?&')
regex_ip = re.compile('[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerName = []
routerIP = []

for line in routerPage:
    if regex_name.search(line) != None:
        routerName.append(str(regex_name.search(line).group()).replace('/cfg/\', \'name=', '').rstrip('&'))
    if regex_ip.search(line) != None:
        routerIP.append(str(regex_ip.search(line).group()))

final = [['Hostname', 'IP Address']]
i = 0
while i < len(routerName):
    final.append([routerName[i], routerIP[i]])
    i += 1

for PC in final:
    print PC[0], PC[1]
```

---

### Post by SaaTeeVaaGreen on 2009-06-09
this works great, but it returns all active users and users that have connected previously but are not currently connected. is there any way to get it to ignore inactive users, such as to ignore lines that begin 'Inactive Desktop'?

i did have a look through the documentation on the website, but its gonna take more than quick flick through for me to work this out myself!

---

### Post by Celauran on 2009-06-09
Better?

```
#!/usr/bin/env python

import re
import urllib

username = "username"
password = "password"
routerURL = "URL without http://"
protocol = "http://"

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

regex_name = re.compile('Active.*?<\/a>')
regex_ip = re.compile('[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerName = []
routerIP = []

for line in routerPage:
    if regex_name.search(line) != None:
        routerName.append(str(regex_name.search(line).group()).replace('Active Desktop\' border=\'0\'>', '').replace('</a>', ''))
    if regex_ip.search(line) != None:
        routerIP.append(str(regex_ip.search(line).group()))

final = [['Hostname', 'IP Address']]
i = 0
while i < len(routerName):
    final.append([routerName[i], routerIP[i]])
    i += 1

for PC in final:
    print PC[0], PC[1]
```

---

### Post by SaaTeeVaaGreen on 2009-06-09
fantastic! this is working perfectly. have added it to conky and am getting exactly the result i was hoping for!:D 

thank you so much, you are a :KS if i could i would buy you a pint to say thanks! your help is really appreciated!

---

### Post by SaaTeeVaaGreen on 2009-06-09
apologies Celauran, i got ahead of myself. although the script is returning the correct active users it is not returning their corresponding ip addresses. i tried amending line 23 to match line 21 (apart from the routerName/routerIP part of course), thinking it was 'Active Desktop' part which was missing causing the problem, but its obviously not this simple as i now get this error in terminal:

> me@mylaptop:~$ python check.py
Traceback (most recent call last):
  File "check.py", line 23, in <module>
    routerIP.append(str(regex_name.search(line).group()).replace('Active Desktop\' border=\'0\'>', '').replace('</a>', ''))
AttributeError: 'NoneType' object has no attribute 'group'

any suggestions?

---

### Post by Celauran on 2009-06-09
Oh, right. I initially pulled all names and IPs, so they were lining up nicely. Now I'm pulling some names but still all IPs.

Getting kludgier every time:
```
#!/usr/bin/env python

import re
import urllib

username = "username"
password = "password"
routerURL = "URL without http://"
protocol = "http://"

routerPage = urllib.urlopen(protocol + username + ":" + password + "@" + routerURL).readlines()

regex_name = re.compile('\/cfg\/\', \'name=.*?&')
regex_ip = re.compile('[0-9]{1,3}(\.[0-9]{1,3}){3}')

routerName = []
routerIP = []
routerActive = []

routerName.append('Gateway')
routerActive.append(False)

for line in routerPage:
    if regex_name.search(line) != None:
        routerName.append(str(regex_name.search(line).group()).replace('/cfg/\', \'name=', '').rstrip('&'))
    if regex_ip.search(line) != None:
        routerIP.append(str(regex_ip.search(line).group()))
    if re.search('Active Desktop', line) != None:
        routerActive.append(True)
    if re.search('Inactive Desktop', line) != None:
        routerActive.append(False)

final = [['Hostname', 'IP Address', 'Active']]
i = 0
while i < len(routerName):
    final.append([routerName[i], routerIP[i], routerActive[i]])
    i += 1

for PC in final:
    if PC[2] == True:
        print PC[0], PC[1]
```

---

### Post by SaaTeeVaaGreen on 2009-06-10
Perfect! works like a charm! once again, thanks very much for sorting this for me, much appreciated!

---

### Post by TideMan on 2009-06-14
I've been trying the Python script out with my router, but I'm having trouble with the regex, even though mine seems easier than the others posted in this thread.

Here's my router page:
```
["<html><title>DHCP Active IP Table</title><STYLE type=text/css>TD {FONT: 8pt Arial,Helvetica,sans-serif; COLOR: black} </STYLE><body bgcolor=white onLoad=window.focus()><center><table width=100% border=0 cellspacing=1><tr><td colspan=2 valign=middle><font size=2><b>DHCP Active IP Table</td><td align=right><form><input style='font-family:arial' type=button value=' Refresh ' onClick=window.location.replace('DHCPTable.htm')></form></td></tr></table><table width=100% border=0 cellspacing=1><form name=F1 method=get action=Gozila.cgi><input type=hidden name='DHCPTable.htm' value=255><input type=hidden name=hid_returnPoint value=''><tr><td align=right colspan=2><font face=arial size=2>DHCP Server IP Address:</td><th><font face=verdana color=green size=2>192.168.1.1</th></tr><tr align=middle bgcolor=b3b3b3><th><font face=arial size=2 color=#ffffff>Client Hostname</th><th><font face=arial size=2 color=#ffffff>IP Address</th><th><font face=arial size=2 color=#ffffff>MAC Address</th><th><font face=arial size=2 color=#ffffff>Interface</th><script language=javascript>var tabData = new Array( 'RaidMax', '192.168.1.100', '00-1f-d0-a7-01-e3', 'Ethernet', '100' , 'xcase', '192.168.1.101', '00-1f-d0-99-12-92', 'Ethernet', '101' , 'BlueFront', '192.168.1.102', '00-14-85-d4-cc-6a', 'Ethernet', '102' , 'Benji', '192.168.1.103', '00-0f-ea-8d-31-a0', 'Ethernet', '103' , 'Athlon1700', '192.168.1.104', '00-14-85-d4-d9-9a', 'Ethernet', '104' );if(tabData.length >= 5){document.write('<th><input type=submit value=Delete></th></tr>');for(i=0; i<tabData.length-4; i+=5)document.write('<tr bgcolor=cccccc align=middle><td>'+tabData[i]+'</td>'+'<td>'+tabData[i+1]+'</td><td>'+tabData[i+2]+'</td>'+'<td>'+tabData[i+3]+'</td><td><input type=checkbox name=sel_dhcpDelete'+tabData[i+4]+'></td></tr>');}else{document.write('</tr><tr bgcolor=cccccc align=middle><td>None</td><td>None</td><td>None</td><td>None</td></tr>');}</script></form></table></center></body></html>"]
```

All I need to do is to isolate the bit between 'new Array(' and the succeeding ')', then I should be able to extract the data quite easily using ip = ip.split(',').

Can anyone give me a hint, please?

---

### Post by Celauran on 2009-06-14
> **TideMan said:**
> I've been trying the Python script out with my router, but I'm having trouble with the regex, even though mine seems easier than the others posted in this thread.

All I need to do is to isolate the bit between 'new Array(' and the succeeding ')', then I should be able to extract the data quite easily using ip = ip.split(',').

Can anyone give me a hint, please?

```
regex = re.compile('Array\(.*?\)')
```

---

