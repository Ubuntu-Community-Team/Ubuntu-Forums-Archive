---
title: "How I solved the dilemma of the HP1000 Laser Jet 11.04"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by JoannePHook on 2011-05-28
Being relatively new to Ubuntu, all I can say is that it is a totally different world than using Windows. For me, the biggest problem I had was getting my printer to function. You see, I have two systems running Ubuntu, one on V10.10 (Lucid Lynx) and this one running 11.04 (Natty Narwal). On my other computer, getting the correct driver and patches was no big issue as I had solved the problem with V9.10 (Karmic Koala). However, I was not able to get the hplip 3.11.5 that downloaded with the upgrade to install properly. Here is how I worked things out:

1. Open Firefox and go to the HP home page: and selected Support and Drives: [http://www8.hp.com/us/en/support-drivers.html](http://www8.hp.com/us/en/support-drivers.html)

2. Select the drivers and software tab:
    [IMG]http://www8.hp.com/us/en/support-drivers.html[/IMG]
[INDENT]Enter the model number and click on the search tab[/INDENT]

3. When the next screen comes up, select Linux as the operating system which will take you to the following screen. Scroll down until you see the maroon box labeled Linux Drivers and select Obtain Software at the right-hand side of the block.
[IMG]http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=45675&prodTypeId=18972&prodSeriesId=45674&swLang=8&taskId=135&swEnvOID=2020[/IMG]

4.This will lead you to a redirect screen: Click on the "Click To Continue" gadget and you will be redirected to the Open Source and Linux from HP page

5. Click on the "»  	Supported HP printing devices" tab

6. This will take you to the "HP Linux Imaging and Printing" home page

7. Select the "Install wizard" option in the lower left-hand side of the screen. On the next page there will questions for Distribution, version of the distribution, printer type and model. Select the appropriate information and hit step 5: "Next"

8. Click the next to download hplip 3.11.5.run file The driver will download to the default "downloads" file in your home file.

9. I moved the downloaded file to the desktop and then right clicked on the icon and clicked the "Properties" option. 

10. In the properties box, I checked the "Allow Executing file as program" box at the "Execute" location of the permissions tab of the properties drop down.

11. I then double clicked the hplip-3.11.5 icon and then clicked the run in terminal option of the box that popped up.

12. At the terminal level, after the file extracted, I entered the letter "a" at the command prompt, entered my password and then allowed the process to continue to reboot. 

13. After reboot, there is still one patch that needs to be downloaded and installed. To get to this, double-click the blue and white HP icon that will now appear in the top banner of the desktop

14. After the screen this brings up displays, double click the "Install required Plugin option"
[INDENT]This will bring up another screen with the licensing agreement and continue options. Click the agree button and then continue and the patch will load.[/INDENT]

15. After the patch installs, print a test page to verify that the printer is functional.
[INDENT]If the page does not print, reboot the system and then retry a test page. If you hear the printer activate during the latter part of the reboot, you are most likely home free anyway.[/INDENT]

My Printer is now operating properly and we are happy campers.

---

