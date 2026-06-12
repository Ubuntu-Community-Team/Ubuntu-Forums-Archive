---
title: "I've tried everything... twice! But WoW still doesn't work."
date: 2009-06-15
forum: New to Ubuntu
---

### Post by rtooles on 2009-06-15
I recently switched over to Ubuntu 9.04 from Windows XP and even after reading forum after forum and walk through after walk through I find myself unable to play World of Warcraft. I was able to install the game but whenever I try to run it Ubuntu just sort of restarts. I've tried messing with the wtf.config file but I had to make the file myself since the game wouldn't start and make it automatically, so that could have something to do with it. I put **SET gxAPI "opengl"**, **SET ffxDeath "0"** and **SET ffxGlow "0"** into the wtf.config file and still nothing happens.
I'm using a Toshiba Satellite laptop and when I use**lspci | grep VGA** in the terminal it says **VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)**. I've gone into **Hardware Drivers** and after it searches for drivers it gave me a list with **Software Modem** on it but it wasn't activated so I had it installed and activated. I don't know if that has anything to do with my problem or not.
When I installed WoW I followed the **[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) **walk through.
I don't know whether half this stuff even has anything to do with my problem because I'm new to Ubuntu and Linux but I'm a quick learner and I'm looking forward to becoming more experienced with it.

---

### Post by bhadotia on 2009-06-15
Try starting the game from the terminal and post any warnings/errors/messages that you see there, this might help people in solving your problem.

Personally I'm not that much of a gamer so can't help you any further. Also I recommend that you install wine from the official ubuntu repositories and not from the WineHQ repo as advised in the [wiki]("https://help.ubuntu.com/community/WorldofWarcraft"). I also recommend going the through the wiki once more very thoroughly  and as patiently as you can (this is one thing that used to give lot of headaches in the beginning- not reading the wiki's completely and properly). And as you are a quick learner, I think you will find your way through this easily (by some smart googling and patient reading).

And almost forgot, welcome to ubuntu;)

---

### Post by rtooles on 2009-06-15
I used **wine "C:\Program Files\World of Warcraft\Launcher.exe"** to open the game from the terminal and this is everything that came up...

```
fixme:shdocvw:PersistStreamInit_Load (0x1417c8)->(0x33d9a0)
fixme:shdocvw:OleControl_FreezeEvents (0x1417c8)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x1417c8)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x141dd0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141dd0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141db0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141db0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141db0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141db0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x141db0): WIN32_FIND_DATA is not yet filled.
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33c824
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x240e888, overlapped 0x240e890): stub
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[16fad0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x141868)->((null) 1 0x33cdbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 25 2 0x33cdd0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 26 2 0x33cdd0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x141868)->(0x33ce0c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33cee0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x147ed8)->(L"" L"" 0 0x33cf18)
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 29 2 0x33d4bc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x141868)
fixme:shdocvw:ClientSite_GetContainer (0x141868)->(0x33d2fc)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:InPlaceFrame_SetStatusText (0x141868)->(0xb7ed0051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 25 2 0x33d230 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 26 2 0x33d230 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x141868)->((null) 28 2 0x33df3c (nil))
0[16fad0]: NPN Logging Active!
0[16fad0]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[16fad0]: NPP Logging Active!
0[16fad0]: nsPluginHostImpl::ctor
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented

```after all that the launcher did successfully load but not the game still wont.
And ty for the welcome.

---

### Post by JordyD on 2009-06-15
Do you have your video card's driver installed?

---

### Post by donkyhotay on 2009-06-15
Try posting this in the [ubuntu wine forum](http://ubuntuforums.org/forumdisplay.php?f=313) which is where the question really belongs.

---

### Post by rtooles on 2009-06-15
I had my video cards driver installed before I formatted and switched to Ubuntu. But I read that Intel cards are very well supported by Linux because they contribute their codes a lot. And when I went into the **Hardware Drivers** utility it only showed the **Software Modem **in the list of hardware that require drivers. And then I proceeded to activate the **Software Modem** and it updated and installed or whatever and it is activated at the moment. So I don't know whether or not the driver is installed is their some other way I can check besides using **Hardware Drivers** or am I doing something wrong with the program?

---

### Post by SunnyRabbiera on 2009-06-15
Actually there are some cards that dont work so well right now with Ubuntu 9.04, intel especially.
There have been a lot of backsteps for Ubuntu Jaunty, thats why I dont use it.

---

### Post by sandyd on 2009-06-15
have you tried the latest (unstable) version of WINE that can be obtained here?
[http://www.winehq.org/download](http://www.winehq.org/download)

p.s. You might wanna look here...
[http://www.wowwiki.com/Wine#Distribution-specific_methods](http://www.wowwiki.com/Wine#Distribution-specific_methods)

and here.
[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

---

### Post by bhadotia on 2009-06-17
> **carlee said:**
> have you tried the latest (unstable) version of WINE that can be obtained here?
[http://www.winehq.org/download](http://www.winehq.org/download)

p.s. You might wanna look here...
[http://www.wowwiki.com/Wine#Distribution-specific_methods](http://www.wowwiki.com/Wine#Distribution-specific_methods)

and here.
[http://appdb.winehq.org/appview.php?iAppId=1922](http://appdb.winehq.org/appview.php?iAppId=1922)

He has used the latest version:
> When I installed WoW I followed the [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) walk through.
- you should read the links given by the OP- that is why I advised him to install wine from the official repos:
> Also I recommend that you install wine from the official ubuntu repositories and not from the WineHQ repo as advised in the wiki.

Please don't take it in a negative manner but you should not give confusing suggestions.

---

