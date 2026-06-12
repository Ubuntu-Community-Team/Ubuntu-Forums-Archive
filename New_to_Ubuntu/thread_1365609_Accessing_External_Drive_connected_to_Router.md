---
title: "Accessing External Drive connected to Router"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by dstjohn on 2009-12-27
I have a Maxtor-300 Gigabyte networked external drive  [192.168.1.6] connected to a Netgear wireless router [192.168.1.1].  When I first connected my Ubuntu computer to the router, i went to Places, Network, Windows Network, Valley View Rd and the Maxtor appeared.  I was able to open it and attach the PUBLIC folder which then appeared on my list of Places for saving and opening documents.

Since I upgraded to 9.10, i am no longer able to see the Maxtor drive under the Windows Network link; I get message:  "Unable to mount Drive" after clicking the Valley View Rd folder (this is my local area network established on my Windows PC).

Since the Maxtor is connected directly to the Netgear router and not involved with a Windows Network at all, can't i connect directly to the Maxtor?  How do I do that?
:confused:

---

### Post by Morbius1 on 2009-12-27
Open **Terminal**
Type **smbtree**
Type **smbclient -l whatever_the_nas_ip_address_is**
 
Post any errors that it might output.

---

### Post by dstjohn on 2009-12-27
"opening ValleyViewRd"
"unable to mount location"
          'failed to receive share list from server'

what 'server' are they talking about?
PC->router->Maxtor is the connection (no server involved)

---

### Post by Morbius1 on 2009-12-27
A NAS device has a server on it - oddly enough it's usually a linux samba server.

See if you can access it by ip address:

Press **Alt+F2**
Type **nautilus smb://192.168.0.100**
[COLOR=Blue]*Change 192.168.0.100 to the actual ip address of the NAS.*[/COLOR]

If it connects and you can see the share, then bookmark it. It will show up under "Places" in Nautilus.

---

### Post by dstjohn on 2009-12-27
danube@study-desktop:~$ smbtree
Enter danube's password: 
VALLEYVIEWRD
    \\MAXTOR-300G            Maxtor-300G
cli_start_connection: failed to connect to MAXTOR-300G<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

---

### Post by dstjohn on 2009-12-27
> **Morbius1 said:**
> Open **Terminal**
Type **smbtree**
Type **smbclient -l whatever_the_nas_ip_address_is**
 
Post any errors that it might output.
***************************
having trouble with smbclilent command:
***************************

_**MY INPUT:**_
$ smbclient -l [http://192.168.1.6](http://192.168.1.6)

_**TERMINAL OUTPUT:**_
Usage: smbclient [-?EgBVNkPe] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-t|--terminal=CODE] [-m|--max-protocol=LEVEL]
        [-T|--tar=<c|x>IXFqgbNan] [-D|--directory=DIR] [-c|--command=STRING]
        [-b|--send-buffer=BYTES] [-p|--port=PORT] [-g|--grepable]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [-O|--socket-options=SOCKETOPTIONS]
        [-n|--netbiosname=NETBIOSNAME] [-W|--workgroup=WORKGROUP]
        [-i|--scope=SCOPE] [-U|--user=USERNAME] [-N|--no-pass]
        [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|required] [-P|--machine-pass] [-e|--encrypt]
        service <password>

---

### Post by Morbius1 on 2009-12-27
No http:

smbclient -l 192.168.1.6 

and the "l" is a lower case "L"

[COLOR=Blue]EDIT: I'm getting very sloppy here. My apologies that's **smbclient**[/COLOR][COLOR=Blue]** -L 192.168.1.6**[/COLOR]

---

### Post by dstjohn on 2009-12-27
> **Morbius1 said:**
> No http:

smbclient -l 192.168.1.6 

and the "l" is a lower case "L"

*****
still having trouble
*****

[U][B]I ENTERED:
[/B][/U]$ smbclient -l 192.168.1.6

_**TERMINAL RETURNED:**_
Usage: smbclient [-?EgBVNkPe] [-?|--help] [--usage]
        [-R|--name-resolve=NAME-RESOLVE-ORDER] [-M|--message=HOST]
        [-I|--ip-address=IP] [-E|--stderr] [-L|--list=HOST]
        [-t|--terminal=CODE] [-m|--max-protocol=LEVEL]
        [-T|--tar=<c|x>IXFqgbNan] [-D|--directory=DIR] [-c|--command=STRING]
        [-b|--send-buffer=BYTES] [-p|--port=PORT] [-g|--grepable]
        [-B|--browse] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE]
        [-V|--version] [-O|--socket-options=SOCKETOPTIONS]
        [-n|--netbiosname=NETBIOSNAME] [-W|--workgroup=WORKGROUP]
        [-i|--scope=SCOPE] [-U|--user=USERNAME] [-N|--no-pass]
        [-k|--kerberos] [-A|--authentication-file=FILE]
        [-S|--signing=on|off|requ

***
seems '-l' is not expecting an IP address:
***

 [-l|--log-basename=LOGFILEBASE]

---

### Post by Morbius1 on 2009-12-27
> **Morbius1 said:**
> 
[COLOR=Blue]EDIT: I'm getting very sloppy here. My apologies that's **smbclient**[/COLOR][COLOR=Blue]** -L 192.168.1.6**[/COLOR]

And please try the other suggestion while I fumble through this:
> Press **Alt+F2**
Type **nautilus smb://192.168.0.100**
[COLOR=Blue]*Change 192.168.0.100 to the actual ip address of the NAS.*[/COLOR]

If it connects and you can see the share, then bookmark it. It will show up under "Places" in Nautilus.     

---

### Post by dstjohn on 2009-12-27
> **Morbius1 said:**
> A NAS device has a server on it - oddly enough it's usually a linux samba server.

See if you can access it by ip address:

Press **Alt+F2**
Type **nautilus smb://192.168.0.100**
[COLOR=Blue]*Change 192.168.0.100 to the actual ip address of the NAS.*[/COLOR]

If it connects and you can see the share, then bookmark it. It will show up under "Places" in Nautilus.

****
that WORKED!
thanks.
****

is there a way to change the label in the Nautilus list of places?
it now says PUBLIC on 192.168.1.6
when i right-click the 'rename' is not accessible.

---

### Post by Morbius1 on 2009-12-27
> it now says PUBLIC on 192.168.1.6
when i right-click the 'rename' is not accessible. 	

Yes you should have been able to change it's name using the method you just tried. I have not had that happen to me before. Try unmounting it, changing the name, and mounting it again.

---

### Post by dstjohn on 2009-12-27
> **dstjohn said:**
> ****
that WORKED!
thanks.
****

is there a way to change the label in the Nautilus list of places?
it now says PUBLIC on 192.168.1.6
when i right-click the 'rename' is not accessible.
*****************

Interestingly, the link appears in Places when I use Open Office
or just access the link directly; but, if I BROWSE from another
application (like this Forum website to access a picture on the Maxtor)
the link does not appear on the list of 'places'.

Is there another process I need to perform?
or is this a limitation?

---

### Post by Morbius1 on 2009-12-27
Yes, that is / can be a problem. It actually has a mount point in a "hidden" directory:

/home/danube/.gvfs

You have to enable "hidden files": Nautilus > Edit > Preferences > Show hidden and backup files.


[COLOR=Blue]EDIT: BTW, I found another way to edit the name in places that might work if you haven't resolved that issue:

Nautilus > Bookmarks > Edit Bookmarks.[/COLOR]

---

