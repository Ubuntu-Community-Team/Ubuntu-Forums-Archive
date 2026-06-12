---
title: "Installing USB LAN drivers"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by justcop on 2009-03-05
Literally just installed ubuntu and don't have a clue what is going on. Trying to install some drivers that I found for a USB LAN device.
The drivers came with a readme but i don't understand it

I have unpacked the archive but then it says

To install the USB driver for dLAN duo only:



		./configure 

	

		make usbdriver

	

		make install-usbdriver	(as root)

What does this mean. Presumably i have to type this somewhere. I typed it into the terminal but it didn't seem to know what i was talking about. Can anyone help me. Please use language I can understand and start from basics, remember i'm a noob


> 


			README file for



	USB drivers and dlanconfig for devolo dLAN; 



		tested under SUSE Linux and Debian Linux 

		   with kernel versions 2.4 and 2.6



01.03.2005



--------------------------------------------------------------------------------



        Contents



        1.      Overview

        

	2.      Requirements	

	  2.1	SUSE

	  2.2   Debian

	  2.3 	libpcap

	

	3. 	USB-driver installation (for USB connection)

		and the configuration program dlanconfig

	  3.1	Unpack the compressed tar file

	  3.2	Installation

	

	4.	dLAN duo

	  4.1 	Configuration - one-time application 

                (e.g. to test the installation)

	  4.2	Configuration under SUSE Linux — permanent installation	

          4.3	Configuration under Debian Linux — permanent installation

	

	5. 	dlanconfig    

	  5.1	Change password

	  5.2	Overview of the dLAN network



--------------------------------------------------------------------------------



1.      Overview



        This readme file contains information about installing the USB driver 

        and the configuration program dlanconfig under SUSE Linux and 

        Debian Linux.



	We also describe the configuration of the dLAN adapters.

	The dLAN duo can be connected either via Ethernet or USB ports.

	If both are installed, USB has priority.



	

	More detailed information about Linux commands is available in the 

        man pages. These are accessed by entering: man ifconfig.  



	

--------------------------------------------------------------------------------

2. 	Requirements

	

	First of all check that your system and installation are optimised:





	2.1	SUSE





	SUSE users can use the YAST program to set up the required system 

        components or to check that they are selected in advance. Use the SUSE 

        menu system to select -> Yast and enter your “root” password. In the 

        selection dialogue 'Install and Remove software' choose the 'Selections' 

        filter for a list of all of the system components. 



        To install the USB driver and the configuration program dlanconfig, 

        the following system components must be selected: 

   

		'C/C++ Compiler and Tools' 

		

		'Kernel Development'	(for installing the USB driver)





	2.2	Debian



	Debian users wishing to install the USB driver need the appropriate 

        kernel-headers-xxx, which must be installed in advance. You will find 

        the exact description (e.g. kernel-headers-2.4.27) by entering 

        'uname -a'. Type in the following command to install the kernel 

        headers:

		

		apt-get install kernel-headers-xxx 



	Depending on the configuration, the subsequent installation takes place 

        either automatically from the CD or from the Internet, assuming you 

        have access.





	2.3 	libpcap



	libpcap is a library used by network sniffer programs. It offers these 

        programs an interface for processing and analysing data packets in 

        networks. You will need this library if you translate or write this 

        type of software yourself or if you wish to use the dlanconfig 

        configuration program. 



	Under SuSE Linux, the latest libpcap library is installed as standard. 

        We advise you to check you installation anyway.



	Debian users will have to install the libpcab library themselves. Do 

        this by entering the following command:

		

		apt-get install libpcap0.8-dev 



	Depending on the configuration, the subsequent installation takes place 

        either automatically from the CD or from the Internet, assuming you have 

        access. 



	Note: The devolo package includes a source text version of the libpcap 

        library. You should use this source text version if you have a different 

        distribution which does not include libpcap.  

	  

--------------------------------------------------------------------------------



3. 	USB-driver installation (for USB connection) and the configuration program dlanconfig



	3.1 	Unpack the compressed tar file



	The following command unpacks the compressed tar file on your local 

        computer:

		

		tar xzvf dLAN-linux-package-1.2.tar.gz





	3.2	Installation



	After unpacking the tar file, change to the subdirectory dlanconfig and 

        continue with the installation as follows:



	There are three ways to carry out the installation:



		- The dLAN configuration program dlanconfig only

		- The USB driver for dLAN duo only

		- The dLAN configuration program dlanconfig and the USB driver





	To install the program dlanconfig only:

			

		./configure 

	

		make cfgtool

	

		make install-cfgtool	(as root)

	



	To install the USB driver for dLAN duo only:



		./configure 

	

		make usbdriver

	

		make install-usbdriver	(as root)





	To install dlanconfig and the USB driver:



		./configure 

	

		make

	

		make install 		(as root)

	



	Note:  Entering the following command will cause the USB driver to be 

        automatically loaded after a restart:

		

		cd driver

	

		make installboot	(as root)



	

	Note: If error messages are displayed or if the installation aborts, 

        check that your system meets with the system requirements.  

	 

--------------------------------------------------------------------------------

	

4. 	dLAN duo



	The dLAN duo can be connected either via Ethernet or USB ports.

	If both are installed, USB has priority.



	After you install the USB driver from devolo, your computer will 

        recognise all connected dLAN duo adapters as network 

        interfaces. This means that a dLAN duo can be treated like 

        any other interface, such as an Ethernet port, for example.

	Entering the command 'ifconfig -a' displays all network interfaces. 

        Each dLAN duo adapter has an identifier that consists of 

        'dlanusb' and  a unique number (e.g. "0" for the first device, "1" for 

        the second, etc.).



	Note: The command 'ifconfig -a' can only be executed as "root".  





	4.1 	Configuration - one-time application 

                (e.g. to test the installation)



	Note: All of the IP addresses named here are examples only.





	After listing all of the network interfaces with the command 

	'ifconfig -a', continue with the configuration with the following 

	example entries: 





		ifconfig dlanusb0 198.168.0.1 netmask 255.255.255.0 up 



	

	Note: Make sure that the new IP addresses are not already being used in

	your network and that they lie within your existing range of IP

	addresses! 





	4.2 	Configuration under SUSE Linux — permanent installation	



	Note: This procedure can only be executed as "root". 



	For the permanent installation of the dLAN duo under SUSE 

	Linux, you should create a text file with the necessary information for 

	the adapter. 

	Enter the following information with any text editor (e.g. edit, pico):



	- if IP addresses are to be assigned dynamically: 



		BOOTPROTO='dhcp'     

		STARTMODE='hotplug'  	



	Finally, the file is saved under the unique identifier for the 

	dLAN duo adapter as follows:



 	/etc/sysconfig/network/ifcfg-dlanusb0    

 

	

	- if IP addresses are to be assigned statically:



		BOOTPROTO='static'

		STARTMODE='hotplug'

		IPADDR='192.168.0.1'

		NETMASK='255.255.255.0'



	Note: Make sure that the new IP addresses are not already being used in

        your network and that they lie within your existing range of IP

        addresses!  

	

	Finally, the file is saved under the unique identifier for the 

        dLAN duo adapter as follows:

	

	/etc/sysconfig/network/ifcfg-dlanusb0    





	To define a gateway, create the file

	/etc/sysconfig/network/ifroute-dlanusb0 

        and enter the following information:





		default 192.168.0.253 - -  

 

	

	Note: Make sure that the IP address is the same as that for your 

        gateway. In most cases the network router is the gateway.



	



	To set the DNS server edit the file /etc/resolv.conf as follows:



	

		nameserver 192.168.0.253 

                (IP address corresponds to that of the DNS server)





	Note: Ensure that the IP address corresponds to that of your DNS server.

        In most cases the network router is the DNS server.





 	

	Note: dLAN duo adapters cannot be configured graphically with

        Yast. 



  

	4.3 	Configuration under Debian Linux — permanent installation	



	Note: This procedure can only be executed as "root".   



	Under Debian Linux, the following information is appended to the file

        '/etc/interfaces':



	- if IP addresses are to be assigned dynamically: 



		auto dlanusb0		

		iface dlanusb0 inet dhcp





	- if IP addresses are to be assigned statically:



		auto dlanusb0	

 		iface dlanusb0 inet static

		address 192.168.0.1

      		netmask 255.255.255.0

      		gateway 192.168.0.253	(only required for Internet access)		





	The file '/etc/resolv.conf' must be edited to ensure that the name

        resolution is executed correctly. Enter the IP address for the DNS

        server into this file, e.g.





		nameserver 192.168.0.253	(only required for Internet

                access)





	Note: Ensure that the IP address corresponds to that of your DNS server.

        In most cases the network router is the DNS server.



	

	

	Note: Operating multiple network interfaces can potentially cause

        problems with DNS and routing. We recommend the use of DHCP for the

        assignment of IP addresses so that the DNS and gateway are adapted

        automatically.



--------------------------------------------------------------------------------



5.	dlanconfig    



	Note: The following procedure can only be executed as "root". 



	Entering 'dlanconfig' allows you to configure a HomePlug network. The

        following entry is an example that adds your first local dLAN adapter

       (dlanusb0) to your network:     	



		/usr/local/sbin/dlanconfig dlanusb0



	Note: If a local dLAN adapter is connected via Ethernet, then

        dlanconfig will be started with the identifier of the appropriate

        network card, i.e. if it is connected to the first network card, 

	then the entry is as follows:



		 /usr/local/sbin/dlanconfig eth0

	

	A menu assists you to set the network password for the local and/or

        remote dLAN devices. You also have an overview of all dLAN devices

        installed in your network.  



	5.1	Change password



	You can change the HomePlug password for the local dLAN adapter in the

        menu by selecting the option 'Set local network password' and entering

        the new network password. You will then see a brief confirmation if the

        password was changed without error.

	

	You can change the HomePlug password for a remote dLAN adapter in the

        menu by selecting the option 'Set remote network password'. Enter the

        new network password and the Security ID of the remote dLAN adapter. The

        Security ID is printed on the back of every dLAN adapter. Please observe

        that entering the Security ID (XXXX-XXXX-XXXX-XXXX) is case sensitive.

        You will then see a brief confirmation if the password was changed

        without error.



	5.2 	Overview of the dLAN network



	For an overview of all of the remote dLAN adapters installed in your

        dLAN network, use the menu to access the option 'List remote devices'.

        dlanconfig also displays the connection rates between the local and the

        remote dLAN devices.

	If a remote dLAN adapter is highlighted with the * symbol, then the

        connection rate value has not been updated.



--------------------------------------------------------------------------------



---

### Post by Idaho Dan on 2009-03-05
make install-usbdriver (as root)
This means you have to prefix the command with sudo to run.
So you would type    sudo make install-usbdriver    

I hope this helps.

---

### Post by justcop on 2009-03-06
I have managed to follow the instruction without errors but my device still doesn't show up. Once the drivers have been installed how do I add the device?

---

### Post by OffAxis on 2009-03-06
what does 
```
lsusb 
```
give you? (it should list every usb device you have plugged in)

---

