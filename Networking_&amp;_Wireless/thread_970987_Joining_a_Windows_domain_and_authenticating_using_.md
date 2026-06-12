---
title: "Joining a Windows domain and authenticating using 802.1x on a wired network"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by Modeverything on 2008-11-04
Hi everyone!

For a while, I tried to figure out a way to get my Ubuntu machine to work on our corporate network, which is a MS Windows environment and uses 802.1x machine based certificate authentication for network access.

I was unable to find any how-to's to do something like this, but I did manage to find enough information here and there to to figure out how to make it work.  The main issue is that most organizations don't use machine based certificate authentication, but rather user authentication; but for those that were in my situation, I hope this guide helps.

Feel free to give me any feedback of any issues you come across while getting this to work.

This document is written from the point of view of our corporate network, like our in-house Certificate Authority and so forth, so you may need to substitute something like Verisign for yours.

Also, apparently some of the formatting was lost in my copy and paste from my word document to this forum, so hopefully it will make sense.  I was also going to attach a document of it so it would be easier to read, but my 29k document exceeded the 19k limit of the forums; sorry.









[I]
Disclaimer:  This guide is written from the perspective of the Linux Ubuntu 8.04 distribution.  To make this work with other Linux or Unix distributions, some changes may need to be made.[/I]

The two main things that are necessary for your Linux machine to authenticate over 802.1x is a client certificate and an account in the Windows domain.  During the authentication process, the Linux client presents it's computer certificate to the switch, which in turn presents it to the RADIUS server who verifies the certificate, and verifies the computer account the certificate is assigned to in Active Directory.  If the certificate and the computer account are valid, then the RADIUS server approves the authentication request sending it back to the switch, which in turn authenticates the port the Linux box is connected to.


The first thing that needs to be done is to join your Linux computer to the Windows domain.  Since Linux cannot natively join a Windows domain, we must download the necessary software to allow us to do this.  Likewise makes software to allow us to do just this.  To install this on Ubuntu it is very simple, just follow these steps:
1)sudo apt-get update
2)sudo apt-get install likewise-open
3)sudo domainjoin-cli join <enter the FQDN of your domain here> <enter your admin account here, you may use the format [email]user@domain.com[/email]>  You should also be able to use the GUI version by going to System &#8594; Administration &#8594; Likewise.
4)sudo update-rc.d likewise-open defaults
5)sudo /etc/init.d/likewise-open start

If you are not running Ubuntu, you may download the software here [http://www.likewisesoftware.com/products/likewise_open](http://www.likewisesoftware.com/products/likewise_open) .
You may now log out and log back in using your domain account.  I believe that either format of [email]user@domain.com[/email] and *domain\user* both work.  I will test this later.

There are three files located on the Linux machine that must be configured correctly in order for this authentication to take place.  These three files are:
1)/etc/wpa_supplicant.conf
2)/etc/network/interfaces
3)/etc/openssl/openssl.cnf

First we will configure the software to allow our Linux machine to use a client certificate to authenticate to an 802.1x enabled network; wpa_supplicant will be used for this.
Follow these steps to configure your wpa_supplicant.conf file:
1)sudo gedit /etc/wpa_supplicant.conf
2)Paste the following into the file and save it:

# Where is the control interface located? This is the default path:
	ctrl_interface=/var/run/wpa_supplicant

	# Who can use the WPA frontend? Replace "0" with a group name if you
	#   want other users besides root to control it.
	# There should be no need to chance this value for a basic configuration:
	ctrl_interface_group=0

	# IEEE 802.1X works with EAPOL version 2, but the version is defaults 
	#   to 1 because of compatibility problems with a number of wireless
	#   access points. So we explicitly set it to version 2:
	eapol_version=1

	# When configuring WPA-Supplicant for use on a wired network, we don’t need to scan for 	#wireless access points. See the wpa-supplicant documentation if you are authenticating through 	#802.1x on a wireless network:
	ap_scan=0

	network={ 
		ssid="<enter any name here, it doesn't matter>" 
		key_mgmt=IEEE8021X 
		eap=TLS 
		identity="<FQDN>/computers/<Linux computer name>" 
		client_cert="/etc/ssl/certs/<your authentication certificate name>.pem" 
		private_key="/etc/ssl/private/<your private key name>.pem" 
		}


Now we must edit your interfaces file.  Follow these steps to configure your interfaces file:
1)sudo gedit /etc/network/interfaces
2)Paste the following into the file under the eth0 interface and save it:

# Configure the system to authenticate with WPA-Supplicant on interface eth0
wpa-iface eth0

# In this case we have a wired network:
wpa-driver wired

# Tell the system we want to use WPA-Supplicant with our configuration file:
wpa-conf /etc/wpa_supplicant.conf



The next step is to generate and install your certificates.  We will have to generate a self-signed certificate, then generate a certificate request based on the self-signed certificate we created, then install the certificates.
**Note:  When creating your certificates, whenever it asks for your name, you must provide the name of the computer which will be authenticating.  To be safe, I recommend making the name match the way it is assigned to the computer, including being case sensitive.  If you are unsure how it is assigned to your computer, open a terminal and type hostname.**
Follow these steps:
1)sudo openssl req -x509 -nodes -days <enter in days how long you want the cert valid for> -newkey rsa:1024 -keyout <enter a name for your private key/certificate here>.pem -out <enter a name for your private key/certificate here>.pem
*Example: sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout privcert.pem -out privcert.pem*
2)openssl req -new -newkey rsa:1024 -nodes -keyout <enter a name for your private key here>.pem -out <enter a name for your certificate request here>.pem
*Example: sudo openssl req -new -newkey rsa:1024 -nodes -keyout privkey.pem -out certreq.pem*

All of the certificates created are placed in your home directory (/home/<username>).  The next part is to request a certificate from your CA using the certificate request that was created in the previous step.  This will need to be done on a Windows machine, since for some reason Linux and Windows don't get along too well when requesting and downloading certificates; I just found it easier to email the certificate request to myself and perform it on a Windows machine.  Follow these steps to complete the certificate request:
1)Go to your home directory on the Linux machine and find your certificate request file
2)Either email the file to yourself or open the file with a text editor (such as gedit) and copy and paste the request into an email and send that to yourself.
3)On a Windows client, open a webpage using IE to your CA's website (such as [http://caname/certsrv](http://caname/certsrv)).
4)Select Request a Certificate
5)Advanced Certificate Request
6)Now open your email and get the certificate request that you emailed yourself.
7)If you emailed yourself the file, open it with notepad and copy and paste the contents into the Base-64 encoded certificate request box.  If you emailed yourself the contents of the certificate request file rather than the file itself, then just copy and paste the request from there into the Base-64 encoded certificate request box.
8)Click Submit and download the certificate in Base-64 form, not DER.
9)Save the certificate to your desktop and name it <your Linux machine name>.pem.  The system will automatically append the .cer to the end of it, so just delete that off.  Linux uses .pem for certificate extensions.
10)Take this file and email it back to yourself.
11)Now, on your Linux machine, get your certificate and save it somewhere (preferably your home folder to keep things organized and together).
12)Now, we need to copy your certificate that you just received to your /etc/ssl/certs folder, and we need to copy your private key/certificate and private key created earlier in your /etc/ssl/private folder.  Now, only root has permission to do this, so you can either do this by command line by typing sudo cp /home/<username>/<certificate>.pem /etc/ssl/private or /etc/ssl/certs.  This can also be done from the GUI by copying and pasting by using the command gksudo and typing in nautilus.  Nautilus is the GUI file browser that Ubuntu uses and it will run this as root allowing you to copy and paste to directories that only root has access to.

Now that our certificates are in place, we need to tell openssl how we want to use the certificates.  To do this, we must edit the openssl.cnf file and tell it to authenticate our Linux machine as a client rather than a user.  To do this follow these steps:
1)sudo gedit /etc/ssl/openssl.cnf
2)Scroll down about half way and you should see a section called [ usr_cert ].  In this section we need the where the nsCertType is defined as “For normal client use this is typical”, and it should have “nsCertType  = client, email” and it will be commented out.  Uncomment this line and delete the email so that it shows “nsCertType = client”.  Now save the file.

Now you should have everything you need configured properly to have a Linux machine running in a Windows domain environment and authenticating using 802.1x.

All that is left now is to restart your networking service so that Linux will use the wpa_supplicant.conf file that is now tied to your eth0 interface and authenticate.  So just run sudo service networking restart.  If you don't get an IP address after your interface comes back up, you can manually request an IP from your DHCP server by typing sudo dhclient.

---

### Post by justhole on 2009-05-01
What about pre-authentication using a computer account with 802.1x?

First off, I got this to work without jumping through all of those hoops using Jaunty. Likewise-open joins you up to a domain just fine, the gui is nice too, and if you have access to a memory stick you can just transfer the SSL cert you need over to your hard drive for use in the wireless 801.x setup.

Here's my issue:

In Windows XP you can check the little box (or use Group Policy to push out the settings), to "authenticate as a computer when computer information is available". This lets you as an Administrator put the computer account into the AD group with access to authenticate on the wireless network. That way, when a user on a laptop starts their computer up - it latches on to the wireless network to pre-authenticate you until you supply user credentials... otherwise there's a catch-22 where you can't authenticate to the network until you connect to the network thing going on...

Using my Ubuntu laptop, I have joined to my AD domain and added the computer account to the appropriate group. But, unless I am hard-wired using an Ethernet connection I still get the "Domain controller unavailable, logging you in using cached credentials error", when logging in. 

Has anyone out there found a way to get Ubuntu 9.04 (or any version) to pre-authenticate to a 802.1x wireless domain using the computer account in Active Directory? 

With only one user on a laptop it's not a huge problem, but if you have multiple users using the same laptop on a wireless network it becomes a problem. Each user has to find a wire & login and get their credential cached before the can login wirelessly.

Any help here would be greatly appreciated!

Justin Kintzele
Network Administrator
Better World Books
[email]justin@betterworldbooks.com[/email]

---

