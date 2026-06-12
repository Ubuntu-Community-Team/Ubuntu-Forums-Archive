---
title: "Why Does Not The Wireless Connection Get Any Internet Access?"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Vara_Prada on 2015-09-02
Hello.

        I have been carefully reading a few web pages related to this topic before deciding to ask [FONT=courier new]Ubuntu[/FONT], but unfortunately now I have to come out of my hide-out and to ask for some more professional help.

        The story goes like this. I have an [FONT=courier new]Asus X-551 M Intel Quad-Core Laptop[/FONT] on which I was usually running [FONT=courier new]Ubuntu[/FONT] inside an [FONT=courier new]Oracle VirtualBox[/FONT] virtual machine. Somehow, it never ran quick enough and sometimes I had to press a key and to wait for a few seconds until anything happened. I have tried to better configure the virtual machine, to no avail.

    Eventually, after a few trial-and-error attempts, I have decided to drop the usage of the virtual machine manager and to run the real thing. What I have done has been to reinstall the [FONT=courier new]Asus Laptop[/FONT] with a brand new [FONT=courier new]Microsoft Windows 10 Home 64-Bit[/FONT] Operating System and to configure it to work as a Wi-Fi HotSpot.

    The solution that I have chosen has been to install the [FONT=courier new]Ubuntu 15.04 *Vivid* for Computers with Less Than Two (2) GigaBytes of Random Access Memory[/FONT] Operating System on another [FONT=courier new]Hewlett-Packard Compaq nx7300 Intel Dual-Core Laptop[/FONT] and to make it wirelessly connect to the [FONT=courier new]Asus Windows[/FONT] laptop. However, whatever I have tried has failed.

    The best situation that I have met so far has been that [FONT=courier new]Ubuntu[/FONT] is wirelessly connecting itself to [FONT=courier new]Windows[/FONT], it says that it is during the course of the connection process ([FONT=courier new]Connecting...[/FONT]), but I do not have any proof that they are really connected.

    A browser such as [FONT=courier new]Mozilla Firefox[/FONT] reports that the [FONT=courier new]Server is not found[/FONT] (which server?) when the Wi-Fi is set in the Infrastructure mode or it plainly gets stuck in [FONT=courier new]Connecting...[/FONT] without doing actually anything visible when the Wi-Fi is set in the Ad-Hoc mode.

    I have also tried to create the Wi-Fi HotSpot on [FONT=courier new]Ubuntu[/FONT] and to make [FONT=courier new]Windows[/FONT] wirelessly connect to it. That time again, [FONT=courier new]Windows[/FONT] was lost in [FONT=courier new]Connecting...[/FONT].

    I have been trying these tricks for Thirty-Five (35) Days in a Row and I am really worn-out now. I see that are other questions similar to this one, but the solutions that they have received have already been attempted without any success. This is why I have decided to write this question and maybe somebody has some clues about what is happening and which I am not yet aware about.

    Of course, I would be happy to find some troubleshooting command-line tools that show what the [FONT=courier new]Ubuntu[/FONT] Wi-Fi is actually doing when it is attempting to connect to [FONT=courier new]Windows[/FONT]. Also, I am eager to provide whatever debugging information is needed.

    This is a Home Network. The DSL Provider is a Dial-Up Broadband Provider. It allows only one connection at a time.

    Currently, I am using a Switch for connecting both Laptops to the Ethernet UTP Cable that goes to the Fibre Optic Device. I am reluctant in purchasing a Wireless Router, since I am not yet fully sure that both the Wireless Chipsets are working.

    I have tested the [FONT=courier new]Hewlett-Packard Laptop[/FONT] using a [FONT=courier new]Microsoft Vista Home Premium 32-Bit[/FONT] Operating System prior to the [FONT=courier new]Ubuntu[/FONT] installation. I was very happy then that [FONT=courier new]Vista[/FONT] did connect itself to the other [FONT=courier new]Windows[/FONT], but somehow I missed opening a web page in [FONT=courier new]Vista[/FONT], so I guess it is the same situation. I guess that I was too happy that the Wireless Connection appeared to be working.

    Both Laptops are connected also with a Ethernet UTP Cable towards the Switch. Pinging might be affected by these cables.

    I remember being thoroughly happy that I have copied a very large file while I was running [FONT=courier new]Vista[/FONT], but I can imagine that [FONT=courier new]Vista[/FONT] might have decided on its own that - due to the size of the transfer - it was better to use the Wires rather than the Wireless Connection.

    With the Wires on, with [FONT=courier new]Windows 10[/FONT] connected to the DSL Provider and with [FONT=courier new]Ubuntu 15.04 *Vivid*[/FONT] wirelessly connected to [FONT=courier new]Windows 10[/FONT], I get the following results. Please let me know if you want other permutations and combinations.

    On [FONT=courier new]Windows 10[/FONT], I have a [FONT=courier new]Cygwin 64-Bit[/FONT] Software Installation. This is what it reports:

```

[FONT=courier new]    Mihai@Sahaj ~
[/FONT][FONT=courier new]    $ uname -a
[/FONT][FONT=courier new]    CYGWIN_NT-10.0 Sahaj 2.1.0(0.287/5/3) 2015-07-14 21:28 x86_64 Cygwin
[/FONT]
```
    
    This is what I get in an [FONT=courier new]Ubuntu[/FONT] Terminal Window:

```

[FONT=courier new]    varada@Ubuntu:~$ ping Sahaj
[/FONT][FONT=courier new]    PING Sahaj.mshome.net (192.168.137.1) 56(84) bytes of data.
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=1 ttl=128 time=2.01 ms
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=2 ttl=128 time=2.12 ms
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=3 ttl=128 time=2.10 ms
[/FONT][FONT=courier new]    ^C
[/FONT][FONT=courier new]    --- Sahaj.mshome.net ping statistics ---
[/FONT][FONT=courier new]    3 packets transmitted, 3 received, 0% packet loss, time 2002ms
[/FONT][FONT=courier new]    rtt min/avg/max/mdev = 2.013/2.081/2.125/0.048 ms
[/FONT]
```
    
    This is with the Wires on. Of course, I can try with the Wires off, but eventually I also want to use them. For Large Data Transfers I prefer to use them. I do not know yet if [FONT=courier new]Ubuntu[/FONT] has Embedded Software Network Algorithms that would decide which Physical Medium to use when transferring data - as it appeared to be happening in the case of the [FONT=courier new]Vista[/FONT] Software Installation.

    As described before, the Two (2) Laptops are on the Same Network.

    It appears that [FONT=courier new]Windows 10[/FONT] automatically sets up its [FONT=courier new]Microsoft Windows Firewall[/FONT] upon its Software Installation.

    Of course, I can disable it completely, but eventually I would need it on. I would require your help in configuring it for granting [FONT=courier new]Ubuntu[/FONT]'s Wireless Connection.

    I have saved Twenty-Two (22) Wireless Links in an [FONT=courier new]Ubuntu[/FONT] Bookmarks Folder:

    2.5.1. "*Installing Broadcom Wireless Drivers - Ask Ubuntu*"

            ```

[FONT=courier new]    [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)[/FONT]

```
    2.5.2. "*[FONT=verdana]Wireless network troubleshooter[/FONT]*"

            ```

[FONT=courier new]    [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-troubleshooting-device-drivers.html)[/FONT]

```
    2.5.3. "*Connect to a wireless network*"

```

[FONT=courier new]    [https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html](https://help.ubuntu.com/stable/ubuntu-help/net-wireless-connect.html)[/FONT]

```

    2.5.4. "*wireless - How to connect and disconnect to a network manually in terminal? - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588](http://askubuntu.com/questions/16584/how-to-connect-and-disconnect-to-a-network-manually-in-terminal/16588#16588)[/FONT]

```

    2.5.5. "*networking - How to install Broadcom wireless drivers offline - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/626642/how-to-install-broadcom-wireless-drivers-offline/626653#626653](http://askubuntu.com/questions/626642/how-to-install-broadcom-wireless-drivers-offline/626653#626653)[/FONT]

```

    2.5.6. "*Cannot get Wireless working by any means on 12.04 (Broadcom Issues) - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/312844/cannot-get-wireless-working-by-any-means-on-12-04-broadcom-issues](http://askubuntu.com/questions/312844/cannot-get-wireless-working-by-any-means-on-12-04-broadcom-issues)[/FONT]

```

    2.5.7. "*WifiDocs/WirelessCardsSupported - Community Help Wiki*"

```

[FONT=courier new]    [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)[/FONT]

```

    2.5.8. "*HardwareSupportComponentsWirelessNetworkCardsBroadcom - Community Help Wiki*"

```

[FONT=courier new]    [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom)[/FONT]

```

    2.5.9. "*bcm4311 ubuntu 15.04 - Google Search*"

```

[FONT=courier new]    [https://www.google.ro/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=bcm4311%20ubuntu%2015.04](https://www.google.ro/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=bcm4311%20ubuntu%2015.04)[/FONT]

```

    2.5.10. "*wireless - Ubuntu 15.04 not working with Broadcom B4311 - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/614141/ubuntu-15-04-not-working-with-broadcom-b4311](http://askubuntu.com/questions/614141/ubuntu-15-04-not-working-with-broadcom-b4311)[/FONT]

```

    2.5.11. "*WifiDocs/Driver/bcm43xx - Community Help Wiki*"

```

[FONT=courier new]    [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?action=show&redirect=BroadcomSTA%28Wireless%29)[/FONT]

```

    2.5.12. "*[SOLVED] Broadcom BCM4313 Wireless Sometimes doesn't Work on Startup [Ubuntu 11.04 64 bit] [Archive] - Ubuntu Forums*"

```

[FONT=courier new]    [http://ubuntuforums.org/archive/index.php/t-1783272.html](http://ubuntuforums.org/archive/index.php/t-1783272.html)[/FONT]

```

    2.5.13. "*Cannot get Wireless working by any means on 12.04 (Broadcom Issues) - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/312844/cannot-get-wireless-working-by-any-means-on-12-04-broadcom-issues#](http://askubuntu.com/questions/312844/cannot-get-wireless-working-by-any-means-on-12-04-broadcom-issues#)[/FONT]

```

    2.5.14. "*networking - Is there a way to get Broadcom 802.11ac WiFi (43b1) working on Ubuntu 12.10? - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/251163/is-there-a-way-to-get-broadcom-802-11ac-wifi-43b1-working-on-ubuntu-12-10](http://askubuntu.com/questions/251163/is-there-a-way-to-get-broadcom-802-11ac-wifi-43b1-working-on-ubuntu-12-10)[/FONT]

```

    2.5.15. "*Linux wireless LAN support*"

```

[FONT=courier new]    [http://linux-wless.passys.nl](http://linux-wless.passys.nl)[/FONT]

[FONT=courier new]    [http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom](http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom)[/FONT]

```

    2.5.16. "*modprobe wl hangs - Google Search*"

```

[FONT=courier new]    [https://www.google.ro/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=modprobe%20wl%20hangs](https://www.google.ro/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=modprobe%20wl%20hangs)[/FONT]

```

    2.5.17. "*BCM4311 Mint 16 - no wireless - no Internet connection*"

```

[FONT=courier new]    [http://comptb.cects.com/bcm4311-mint16-nowireless-nointernet/](http://comptb.cects.com/bcm4311-mint16-nowireless-nointernet/)[/FONT]

```

    2.5.18. "*networking - Wireless Internet not working - cannot activate broadcom proprietary driver - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/345623/wireless-internet-not-working-cannot-activate-broadcom-proprietary-driver](http://askubuntu.com/questions/345623/wireless-internet-not-working-cannot-activate-broadcom-proprietary-driver)[/FONT]

```

    2.5.19. "*Ubuntu Broadcom Wireless does not connect to Internet - Google Search*"

```

[FONT=courier new]    [https://www.google.ro/search?q=%22Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet%22&oq=%22Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet%22&aqs=chrome..69i57.17465311j0j0&sourceid=chrome&es_sm=93&ie=UTF-8#q=Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet](https://www.google.ro/search?q=%22Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet%22&oq=%22Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet%22&aqs=chrome..69i57.17465311j0j0&sourceid=chrome&es_sm=93&ie=UTF-8#q=Ubuntu+Broadcom+Wireless+does+not+connect+to+Internet)[/FONT]

```

    2.5.20. "*Broadcom BCM4401-B0 driver breaks in latest update*"

```

[FONT=courier new]    [http://ubuntuforums.org/showthread.php?t=2115659](http://ubuntuforums.org/showthread.php?t=2115659)[/FONT]

```

    2.5.21. "*networking - Broadcom BCM4401-B0 100Base-TX Issues - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues](http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues)[/FONT]

```

    2.5.22. "*networking - (Ubuntu 15.04) wireless connected but no internet access - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/653355/ubuntu-15-04-wireless-connected-but-no-internet-access](http://askubuntu.com/questions/653355/ubuntu-15-04-wireless-connected-but-no-internet-access)[/FONT]

```

    And Twelve (12) Wired Links, also:

    2.5.23. "*12.04 - How to set up a broadband connection - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/100489/how-to-set-up-a-broadband-connection](http://askubuntu.com/questions/100489/how-to-set-up-a-broadband-connection)[/FONT]

```

    2.5.24. "*[SOLVED] Ethernet card could not be found*"

```

[FONT=courier new]    [http://ubuntuforums.org/showthread.php?t=1722614](http://ubuntuforums.org/showthread.php?t=1722614)[/FONT]

```

    2.5.25. "*[SOLVED] Atheros AR8151 Ethernet on Asus P8H67-V*"

```

[FONT=courier new]    [http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)[/FONT]

```

    2.5.26. "*[SOLVED] Wired ethernet not getting detected [Archive] - Ubuntu Forums*"

```

[FONT=courier new]     [http://ubuntuforums.org/archive/index.php/t-1505697.html](http://ubuntuforums.org/archive/index.php/t-1505697.html)
[/FONT]
```

    2.5.27. "*Ubuntu Broadcom Ethernet does not work - Google Search*"

```

[FONT=courier new]    [https://www.google.ro/search?q=%22Ubuntu+Broadcom+Ethernet+does+not+work%22&oq=%22Ubuntu+Broadcom+Ethernet+does+not+work%22&aqs=chrome..69i57.87007852j0j0&sourceid=chrome&es_sm=93&ie=UTF-8#q=Ubuntu+Broadcom+Ethernet+does+not+work](https://www.google.ro/search?q=%22Ubuntu+Broadcom+Ethernet+does+not+work%22&oq=%22Ubuntu+Broadcom+Ethernet+does+not+work%22&aqs=chrome..69i57.87007852j0j0&sourceid=chrome&es_sm=93&ie=UTF-8#q=Ubuntu+Broadcom+Ethernet+does+not+work)
[/FONT]
```

     2.5.28. "*[plug] HP/Compaq NX5000 Broadcom BCM4401-B0 100Base-TX NIC problem*"

```

[FONT=courier new]    [http://lists.plug.org.au/pipermail/plug/2008-October/078020.html](http://lists.plug.org.au/pipermail/plug/2008-October/078020.html)[/FONT]

```
        
    2.5.29. "*Internet card is not working (broadcom bcm4401-b0)*"

```

[FONT=courier new]    [http://www.linuxquestions.org/questions/slackware-14/internet-card-is-not-working-broadcom-bcm4401-b0-924984/](http://www.linuxquestions.org/questions/slackware-14/internet-card-is-not-working-broadcom-bcm4401-b0-924984/)[/FONT]

```
        
    2.5.30. "*Broadcom BCM4401-B0 100Base-TX Issues - TecHub*"

```

[FONT=courier new]    [http://www.tech.theplayhub.com/broadcom_bcm4401-b0_100base-tx_issues/](http://www.tech.theplayhub.com/broadcom_bcm4401-b0_100base-tx_issues/)[/FONT]

```
        
    2.5.31. "*[SOLVED] unable to connect wired Ethernet Broadcom BCM4401-B0 (Page 1) / Help & Support (Testing/Unstable) / CrunchBang Linux Forums*"

```

[FONT=courier new]    [http://crunchbang.org/forums/viewtopic.php?id=24837](http://crunchbang.org/forums/viewtopic.php?id=24837)[/FONT]

```
        
    2.5.32. "*BCM4401-B0 100Base-TX does not work - Google Search*"

```

[FONT=courier new]    [https://www.google.ro/search?q=BCM4401-B0+100Base-TX+does+not+work&oq=BCM4401-B0+100Base-TX+does+not+work&aqs=chrome..69i57.87402667j0j0&sourceid=chrome&es_sm=93&ie=UTF-8](https://www.google.ro/search?q=BCM4401-B0+100Base-TX+does+not+work&oq=BCM4401-B0+100Base-TX+does+not+work&aqs=chrome..69i57.87402667j0j0&sourceid=chrome&es_sm=93&ie=UTF-8)[/FONT]

```
        
    2.5.33. "*Broadcom BCM4401-B0 driver breaks in latest update*"

```

[FONT=courier new]    [http://ubuntuforums.org/showthread.php?t=2115659](http://ubuntuforums.org/showthread.php?t=2115659)[/FONT]

```

    2.5.34. "*Networking - Broadcom BCM4401-B0 100Base-TX Issues - Ask Ubuntu*"

```

[FONT=courier new]    [http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues](http://askubuntu.com/questions/14970/broadcom-bcm4401-b0-100base-tx-issues)[/FONT]

```
    [B]
    Test 1.[/B] I have disconnected the DSL Provider in [FONT=courier new]Ubuntu[/FONT] with the [FONT=courier new]poff[/FONT] command and then connected [FONT=courier new]Windows[/FONT] with a [FONT=courier new]Digi.BAT[/FONT] File. [FONT=courier new]Ubuntu[/FONT] has automatically and wirelessly connected itself to the [FONT=courier new]Windows10[/FONT] Wi-Fi HotSpot. Afterwards, I have first disabled the [FONT=courier new]Microsoft Windows Firewall[/FONT] on the *Private Networks*. This category includes the [FONT=courier new]Windows10[/FONT] Wi-Fi HotSpot and the [FONT=courier new]Network 3[/FONT] Network that might be the Local Area Network created between the Switch and the Two (2) Laptops. [FONT=courier new]Google Chrome[/FONT] has reported the [FONT=courier new]ERR_ADDRESS_UNREACHABLE[/FONT] error while attempting to connect to the [FONT=courier new]https://mail.google.com/[/FONT] Internet Address.

    **    Test 2.** I have disabled the [FONT=courier new]Microsoft Windows Firewall[/FONT] also on the *Guest or Public Networks*. This category included only one (1) [FONT=courier new]Digi 7[/FONT] Network. [FONT=courier new]Google Chrome[/FONT] has reported the [FONT=courier new]ERR_QUIC_PROTOCOL_ERROR[/FONT] Error while attempting to connect to the [FONT=courier new]https://mail.google.com/[/FONT] Internet Address.

    **    Test 3.** I have removed the Wire from [FONT=courier new]Ubuntu[/FONT]. In a Command Line Terminal Window, the [FONT=courier new]ping[/FONT] command has reported the following lines:

```

[FONT=courier new]    varada@Ubuntu:~$ ping Sahaj
[/FONT][FONT=courier new]    PING Sahaj.mshome.net (192.168.137.1) 56(84) bytes of data.
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=1 ttl=128 time=1.90 ms
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=2 ttl=128 time=2.06 ms
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=3 ttl=128 time=2.12 ms
[/FONT][FONT=courier new]    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=4 ttl=128 time=2.07 ms
[/FONT][FONT=courier new]    ^C
[/FONT][FONT=courier new]    --- Sahaj.mshome.net ping statistics ---
[/FONT][FONT=courier new]    4 packets transmitted, 4 received, 0% packet loss, time 3000ms
[/FONT][FONT=courier new]    rtt min/avg/max/mdev = 1.905/2.041/2.120/0.087 ms
[/FONT]
```
    
    Another attempt from [FONT=courier new]Google Chrome[/FONT] to connect to the [FONT=courier new]https://mail.google.com/[/FONT] Internet Address has led to an [FONT=courier new]ERR_CONNECTION_TIMED_OUT[/FONT] Error.

    **    Test 4.** I forgot to replug the Wire in [FONT=courier new]Ubuntu[/FONT] and run a [FONT=courier new]pon dsl-provider[/FONT] command in order to reconnect it to the DSL Provider, obviously.  An attempt to load the [FONT=courier new]http://askubuntu.com/questions/666392/why-does-not-the-wireless-connection-get-any-internet-access[/FONT] Web Page inside the [FONT=courier new]Google Chrome[/FONT] Web Browser has led this time to the [FONT=courier new]ERR_NAME_NOT_RESOLVED[/FONT] Error.

    What is interesting is that, in order to connect [FONT=courier new]Ubuntu[/FONT] to the DSL-Provider, I had to disconnect [FONT=courier new]Windows 10[/FONT] from the DSL-Provider, after which the [FONT=courier new]Microsoft Windows Firewall[/FONT] has shown another [FONT=courier new]Digi 7[/FONT] active public network in its list. The [FONT=courier new]'7'[/FONT] (Seven) Digit has not been chosen at random; actually, the [FONT=courier new]Microsoft Windows[/FONT] Operating System has kept on incrementing its number since the first attempt to create a [FONT=courier new]Digi[/FONT] Internet Connection, through the [FONT=courier new]Digi 2[/FONT], [FONT=courier new]Digi 3[/FONT], and until the current [FONT=courier new]Digi 7[/FONT], while I was continually removing it and recreating it in order to configure the Wi-Fi HotSpot.

    **    Test 5.** Another attempt to load the [FONT=courier new]http://askubuntu.com/questions/666392/why-does-not-the-wireless-connection-get-any-internet-access[/FONT] Web Page inside the [FONT=courier new]Google Chrome[/FONT] Web Browser after replugging the Wire in [FONT=courier new]Ubuntu[/FONT] has led to the same [FONT=courier new]ERR_NAME_NOT_RESOLVED[/FONT] Error.

    **    Test 6.** I have disconnected and then reconnected [FONT=courier new]Ubuntu[/FONT] from the DSL Provider with the following commands:

```

[FONT=courier new]    varada@Ubuntu:~$ poff
[/FONT][FONT=courier new]    varada@Ubuntu:~$ pon dsl-provider
[/FONT][FONT=courier new]    Plugin rp-pppoe.so loaded.
[/FONT]
```
    
    This time, the [FONT=courier new]http://askubuntu.com/questions/666392/why-does-not-the-wireless-connection-get-any-internet-access[/FONT] Web Page did get loaded correctly within the [FONT=courier new]Google Chrome[/FONT] Web Browser. However, this has been done through the Direct Wired Connection to the DSL Provider and not through the Wireless Connection to the [FONT=courier new]Windows10[/FONT] Wi-Fi HotSpot.

    **    Test 7.** [FONT=courier new]Windows 10[/FONT] is not yet turned on. I am running the [FONT=courier new]pon dsl-provider[/FONT] command and the [FONT=courier new]iwconfig[/FONT] command inside an [FONT=courier new]Ubuntu[/FONT] Command Line Terminal Window:

```

[FONT=courier new]    varada@Ubuntu:~$ pon dsl-provider
[/FONT][FONT=courier new]    Plugin rp-pppoe.so loaded.
[/FONT][FONT=courier new]    varada@Ubuntu:~$ iwconfig
[/FONT][FONT=courier new]    ppp0      no wireless extensions.

[/FONT][FONT=courier new]    wlan0 IEEE 802.11bg         ESSID:        off/any
    Mode:              Managed  Access Point: Not-Associated   Tx-Power    = 20 dBm
    Retry short limit: 7        RTS thr:      off              Fragment thr: off
    Power Management:  off

    lo        no wireless extensions.

    eth0      no wireless extensions.
[/FONT]
```

    I am disconnecting [FONT=courier new]Ubuntu[/FONT] from the DSL Provider with the [FONT=courier new]poff[/FONT] command. Then, I am turning [FONT=courier new]Windows 10[/FONT] on. It creates its own [FONT=courier new]Windows10[/FONT] Wi-Fi HotSpot and [FONT=courier new]Ubuntu[/FONT] automatically gets connected to it. I am running the [FONT=courier new]iwconfig[/FONT] command inside the same [FONT=courier new]Ubuntu[/FONT] Command Line Terminal Window:

```

[FONT=courier new]    varada@Ubuntu:~$ poff
    varada@Ubuntu:~$ iwconfig
    wlan0     IEEE 802.11bg  ESSID:"Windows10"  
    Mode:Managed  Frequency:2.462 GHz  Access Point: 46:27:1E:83: D9:C7
    Bit Rate=12 Mb/s   Tx-Power=20 dBm
    Retry short limit:7   RTS thr: off   Fragment thr: off
    Power Management: off
    Link Quality=70/70  Signal level=-12 dBm
    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
    Tx excessive retries:0  Invalid misc:0   Missed beacon:0

    lo        no wireless extensions.

    eth0      no wireless extensions.
[/FONT]
```
    [FONT=courier new]
Google Chrome[/FONT] reports the [FONT=courier new]ERR_QUIC_PROTOCOL_ERROR[/FONT] Error while attempting to connect to the [FONT=courier new]https://mail.google.com/[/FONT] Internet Address.

    These outputs do not mean much to me. Maybe they are helpful for the readers.

    Also, I was looking for a command that might inspect what is happening after [FONT=courier new]Ubuntu[/FONT] automatically gets connected to [FONT=courier new]Windows 10[/FONT]. Is there any? I mean, besides the Web Browsers such as [FONT=courier new]Mozilla Firefox[/FONT] and [FONT=courier new]Google Chrome[/FONT]. Their diagnostic information does not present much interesting detail.

    For instance, in the *Details* area of information for the [FONT=courier new]ERR_QUIC_PROTOCOL_ERROR[/FONT] [FONT=courier new]Google Chrome[/FONT] Error it was explained that the [FONT=courier new]https://mail.google.com[/FONT] Web Page must have been moved, which is not true. I have just opened it after directly and wiredly connecting to the DSL Provider and it is working just fine. There must be some other troubleshooting tools out there.

    In case there might be some problems from within the [FONT=courier new]Microsoft Windows 10 Home 64-Bit[/FONT] Operating System Side, here is how I am usually connecting to the DSL Provider from within it and how it is automatically creating the Wi-Fi HotSpot.

    I am using a [FONT=courier new]Microsoft Disk Operating System[/FONT] Batch File that I have called as [FONT=courier new]Digi.BAT[/FONT]. Of course, I have desired that it automatically gets started upon the Operating System Start-Up. Somehow, that never happens.

    The Short-Cuts that are placed inside the [FONT=courier new]Startup[/FONT] Menus (both for [FONT=courier new]All Users[/FONT] and for the current user) do not get started upon the Operating System Start-Up, for daunting reasons that are completely baffling me.

    Therefore, I have decided to simply give up the usage of both the [FONT=courier new]Startup[/FONT] Menus and to use the Old and Safe Manual Double-Click upon a Desktop Short-Cut that is pointing towards the Batch File, each time I need to connect to the DSL Provider.

    This is what it is doing:

```

[FONT=courier new]    C:\WINDOWS\system32>C:\Windows\SysWOW64\RASDial.exe Digi <UserName> <PassWord>

[/FONT][FONT=courier new]    Connecting to Digi...
[/FONT][FONT=courier new]    Verifying username and password...
[/FONT][FONT=courier new]    Registering your computer on the network...
[/FONT][FONT=courier new]    Successfully connected to Digi.
[/FONT][FONT=courier new]    Command completed successfully.

[/FONT][FONT=courier new]    C:\WINDOWS\system32>netsh wlan set hostednetwork mode=allow ssid=Windows10 key=<PassPhrase>
[/FONT][FONT=courier new]
[/FONT][FONT=courier new]    The hosted network mode has been set to allow.
[/FONT][FONT=courier new]    The SSID of the hosted network has been successfully changed.
[/FONT][FONT=courier new]    The user key passphrase of the hosted network has been successfully changed.

[/FONT][FONT=courier new]    C:\WINDOWS\system32>netsh wlan start hostednetwork
    
[/FONT][FONT=courier new]    The hosted network started.

[/FONT][FONT=courier new]    C:\WINDOWS\system32>PAUSE
[/FONT][FONT=courier new]    Press any key to continue . . .
[/FONT]
```

    Some more pieces of information from the [FONT=courier new]Microsoft Windows 10 Home 64-Bit[/FONT] Operating System World.

    Inside the "*Control Panel > All Control Panel Items > Network and Sharing Center*" Window, the following pieces of information are displayed:

```

[FONT=courier new]    View your basic network information and set up connections

        View your active networks

            Digi 7                     Access Type: Internet
            Public Network             Connections: Digi

            Windows10                  Access Type: Internet
            Private Network            Home Group:  Ready to Create
                                       Connections: Local Area Connection* 13

            Network 3                  Access Type: No Internet Access
            Private Network            Home Group:  Ready to Create
                                       Connections: Ethernet
[/FONT]
```

        [FONT=courier new]Digi 7[/FONT] is the Seventh ([FONT=courier new]7[/FONT]th) Version of the Wired Connection to the DSL Provider. It has Internet access and it is feeding [FONT=courier new]Windows10[/FONT] bits and crumbles of it. Or at least it should be. I do not know yet how to test this aspect.

        [FONT=courier new]Windows10[/FONT] is the Wi-Fi HotSpot. It should have Internet access obtained from the above-mentioned DSL Provider Connection. It can also create a HomeGroup, but I do not know yet if that would be helpful for the [FONT=courier new]Ubuntu[/FONT] World. Would it be?

        [FONT=courier new]Network 3[/FONT] should be the Local Area Network created by the Loop formed by the Switch and the Two (2) Laptops, Wired between themselves with Ethernet Wires. This one appears not to have Internet access and I am not interested in it having any. I just want to minimize the load on the Wireless Internet Connection that hopefully will be running soon also on [FONT=courier new]Ubuntu[/FONT] and to use this Wired Connection for Large Data Transfers.

    This is kind of it, regarding the loads of information that I am able to paste here from the Two (2) Worlds of [FONT=courier new]Windows 10[/FONT] and [FONT=courier new]Ubuntu 15.04 *Vivid*[/FONT]. Of course, I can go on pasting pieces of information from [FONT=courier new]Properties[/FONT] Windows and from other places, but I prefer to wait for some requests. I am kind of done with investigating. This has extended with a few days the initial investigation period of Thirty-Five (35) Continuous Days.

    One more thing, from within the [FONT=courier new]Ubuntu[/FONT] World. I just want to make sure that there is nothing fishy among the Wi-Fi Connection Settings. These are the details of the Wireless Connection in [FONT=courier new]Ubuntu[/FONT]:

```

[FONT=courier new]    General

        [ v ] Automatically connect to this network when it is available
        [ v ] All users may connect to this network
        [   ] Automatically connect to VPN when using this connection
        
        Firewall zone:                 <Default>

    Wi-Fi

        SSID:                          "Windows10"
        Mode:                          Infrastructure
        BSSID:                         <Nothing>
        Device MAC Address:            <Some Data> (wlan0)
        Cloned MAC Address:            <Nothing>
        MTU:                           Automatic

    Wi-Fi Security

        Security:                      WPA & WPA2 Personal
        Password:                      <Password>

    IPv4 Settings

        Method:                        Automatic (DHCP)
        Addresses:                     <Nothing>
        Additional DNS Servers:        <Nothing>
        Additional Search Domains:     <Nothing>
        DHCP Client ID:                <Nothing>
        [   ] Require IPv4 addressing for this connection to complete

        Routes:                        <Nothing>
            [   ] Ignore automatically obtained routes
            [   ] Use this connection only for resources on its network

    IPv6 Settings

        Method:                        Ignore
        Addresses:                     <Nothing>
        DNS Servers:                   <Nothing>
        Search Domains:                <Nothing>
        IPv6 Privacy Extensions:       Disabled
        [   ] Require IPv6 addressing for this connection to complete
[/FONT]
```

        [FONT=courier new]Ubuntu[/FONT] Proxy Settings.

        *        Mozilla Firefox*

            Just to make sure, I have changed the default setting from [FONT=courier new]Use system proxy settings[/FONT] to [FONT=courier new]No proxy[/FONT], to no avail. [FONT=courier new]Mozilla Firefox[/FONT] continues to report the following Error Message:

```

[FONT=courier new]    Server not found

        Firefox can't find the server at start.ubuntu.com.

        Check the address for typing errors such as ww.example.com instead of [www.example.com]("http://www.example.com")

        If you are unable to load any pages, check your computer's network connection.
    
        If your computer or network is protected by a firewall or proxy, make sure that Firefox is permitted to access the Web.
[/FONT]
```

        *    Google Chrome*

                    [FONT=courier new]Google Chrome[/FONT] is trickier, as usual. He just will not give up easily. While attempting to alter the Proxy Settings, it has opened the [FONT=courier new]chrome://linux-proxy-config/[/FONT] Web Page with the following pieces of information:

```

[FONT=courier new]    When running Google Chrome under a supported desktop environment, the system proxy settings will be used. However, either your system is not supported or there was a problem launching your system configuration.
[/FONT]
[FONT=courier new]    But you can still configure via the command line. Please see man google-chrome-stable for more information on flags and environment variables.[/FONT]

```

    While going towards the Command Line Terminal Window, I have not had any success there, either. Help does not seem to come out easily:

```

[FONT=courier new]    varada@Ubuntu:~$ /usr/bin/google-chrome-stable --help
    No manual entry for google-chrome-stable
    See 'man 7 undocumented' for help when manual pages are not available.
[/FONT]
```
        
    What is interesting is that [FONT=courier new]Google Chrome[/FONT] keeps on shuffling its error codes when it is reporting an error. This time, it has presented the following error to the user, when the [FONT=courier new]https://mail.google.com/mail/[/FONT] Web Page has been attempted to be opened:

```

[FONT=courier new]    This webpage is not available

    ERR_NAME_RESOLUTION_FAILED
    
    Hide details
    
    The webpage at [https://mail.google.com/mail/](https://mail.google.com/mail/) might be temporarily down or it may have moved permanently to a new web address.
[/FONT]
```[FONT=courier new]

[/FONT]    Anyway, [FONT=courier new]Mozilla Firefox[/FONT] has already proven that there is no proxy set up. I have never ever set up a proxy on this machine in [FONT=courier new]Ubuntu[/FONT]. This is a fresh installation, done from a [FONT=courier new]Ubuntu 15.04 *Vivid*[/FONT] Digital Versatile Disk.

    Also, I was attempting to understand the logic in their request to disable a firewall only on the [FONT=courier new]Microsoft Windows 10 Home 64-Bit[/FONT] machine.

    Indeed, logically [FONT=courier new]Ubuntu[/FONT] needs to access [FONT=courier new]Windows'[/FONT] ethereal space, so it needs to cross any firewalls that [FONT=courier new]Windows[/FONT] is maintaining. Now, the [FONT=courier new]Microsoft Windows Firewall[/FONT] is completely disabled, on all the networks.

    What if there is a need also to disable some firewalls inside the [FONT=courier new]Ubuntu[/FONT] World? I have never ever set up any firewalls on this machine in [FONT=courier new]Ubuntu[/FONT]. Are there any firewalls installed in [FONT=courier new]Ubuntu[/FONT] by default that have to be disabled, also?

    Some debugging tips:

```

[FONT=courier new]    varada@Ubuntu:~$ route -n
    Kernel IP routing table
    Destination            Gateway                Genmask              Flags        Metric     Ref    Use    Iface
      0.  0.  0.0            192.168.137.1            0.  0.  0.0      UG            400       0      0      wlan0
    169.254.  0.0              0.  0.  0.0          255.255.  0.0      U            1000       0      0      wlan0
    192.168.137.0              0.  0.  0.0          255.255.255.0      U               0       0      0      wlan0
    varada@Ubuntu:~$ ping -c3 91.189.94.12
    PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.
    From 192.168.137.1 icmp_seq=1 Destination Net Unreachable
    From 192.168.137.1 icmp_seq=2 Destination Net Unreachable
    From 192.168.137.1 icmp_seq=3 Destination Net Unreachable

    --- 91.189.94.12 ping statistics ---
    3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2003ms

    varada@Ubuntu:~$ ping -c3 ubuntuforums.org
    PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
    From Sahaj.mshome.net (192.168.137.1) icmp_seq=1 Destination Net Unreachable
    From Sahaj.mshome.net (192.168.137.1) icmp_seq=2 Destination Net Unreachable
    From Sahaj.mshome.net (192.168.137.1) icmp_seq=3 Destination Net Unreachable

    --- ubuntuforums.org ping statistics ---
    3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2002ms

    varada@Ubuntu:~$ cat /etc/resolv.conf
    # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
    nameserver   127.0.1.1
    search       mshome.net
    varada@Ubuntu:~$ ping 127.0.1.1
    PING 127.0.1.1 (127.0.1.1) 56(84) bytes of data.
    64 bytes from 127.0.1.1: icmp_seq=1 ttl=64 time=0.054 ms
    64 bytes from 127.0.1.1: icmp_seq=2 ttl=64 time=0.066 ms
    64 bytes from 127.0.1.1: icmp_seq=3 ttl=64 time=0.038 ms
    64 bytes from 127.0.1.1: icmp_seq=4 ttl=64 time=0.049 ms
    ^C
    --- 127.0.1.1 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 2998ms
    rtt min/avg/max/mdev = 0.038/0.051/0.066/0.013 ms
    varada@Ubuntu:~$ ping mshome.net
    ping: unknown host mshome.net
    varada@Ubuntu:~$ ping sahaj.mshome.net
    PING Sahaj.mshome.net (192.168.137.1) 56(84) bytes of data.
    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=1 ttl=128 time=2.37 ms
    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=2 ttl=128 time=2.55 ms
    64 bytes from Sahaj.mshome.net (192.168.137.1): icmp_seq=3 ttl=128 time=2.77 ms
    ^C
    --- Sahaj.mshome.net ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2003ms
    rtt min/avg/max/mdev = 2.374/2.568/2.773/0.168 ms
[/FONT]
```[FONT=courier new]


[/FONT]

---

### Post by howefield on 2015-09-02
Hello Vara_Prada  and welcome to the forums.

Many congratulations on your verbosity and magnificent ability to elongate a post. You may want to consider shrinking it down a bit from the almost 3,600 words that it currently is, if you really want other forum members to read and assist. Just a suggestion. :)

---

### Post by slickymaster on 2015-09-02
> **howefield said:**
> Hello Vara_Prada  and welcome to the forums.

Many congratulations on your verbosity and magnificent ability to elongate a post. You may want to consider shrinking it down a bit from the almost 3,600 words that it currently is, if you really want other forum members to read and assist. Just a suggestion. :)

One good way to achieve what howefield mentioned is to download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz", for attaching on the forums.

---

### Post by Vara_Prada on 2015-09-02
Thank you all for your Warm Welcome on this forum. I have instantly run the Script and attached its Output to this Post.

    The initial post is the result of Fourteen (14) Revisions of the Body of the Question that has been asked at the following Uniform Resource Locator:

```

[FONT=courier new]    [http://askubuntu.com/questions/666392/why-does-not-the-wireless-connection-get-any-internet-access](http://askubuntu.com/questions/666392/why-does-not-the-wireless-connection-get-any-internet-access)[/FONT]

```

    Indeed, the Question Body is [FONT=courier new]29,492[/FONT] characters ([FONT=courier new]4,764[/FONT] words) in Size now. My only Goal is to get the Problem Solved.

    Just let me know if I can Provide some more Pieces of Information to you.

    Again, Thanks for a Great Introduction.

---

### Post by Vara_Prada on 2015-09-07
I have just tested with another Single-Core Intel Toshiba Laptop running the Microsoft Windows 8.1 64-Bit Operating System. The issue is still persisting.

I have tried initially without Wiring at all the Third (3rd) Laptop into the Initial Home Local Area Network created between the First Two (2) Laptops. Its Microsoft Windows 8.1 64-Bit Operating System has just not been able to obtain any Internet Access from the Wi-Fi HotSpot maintained by the First (1st) Laptop running the Microsoft Windows 10 Home 64-Bit Operating System. The Wireless Connection has apparently been established, but the "You are not connected to the Internet" message has been printed on the screen to the user.

Therefore, this is not an issue related to the Canonical Ubuntu 15.04 "Vivid" for Computers with less than Two (2) GigaBytes of Random Access Memory Operating System. Even though there might be some issues related to it, in the instance of this Configuration it appears that the Problem resides somewhere in the way that the Various Flavors of the Microsoft Windows Operating Systems are maintaining the Wi-Fi HotSpots and in the way that they are providing them with Internet Access obtained from the Direct Wired Connection to the DSL Provider.

---

