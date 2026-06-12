---
title: "corega WLUSB2GO 54M wireless USB adapter Atheros chipset driver Ndiswrapper"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by twlikes on 2007-02-20
Hello Everyone
I'm hoping someone knows a way to fix my wireless problem, let me explain. 

I'm running Edgy, I have a corega WLUSB2GO 54M wireless USB adapter, using an Atheros chipset.  The madwifi driver for this chipset do not support USB devices, so I had hoped to use Ndiswrapper.

The installation CD that came with the product does not have a driver file,  I was able to cabextract a data1.cab file, but all I got was a lot of junk and no .sys or .inf files,

So I downloaded the updated driver and utility exe from the corega website.

[http://www.corega.com.tw/support/dow...GO_Windows.zip](http://www.corega.com.tw/support/dow...GO_Windows.zip)

Then I used cabextract on the downloaded Setup.exe file and I get this list of files;

ctor.dll
IKernel.dll
IScript.dll
ISProBENT.tlb
objectps.dll
DotNetInstaller.exe
iKernel.rgs
ISProBE9x.tlb
IUser.dll

NO .sys or .inf files?
What gives??
I try to do a cabextract/unshield on the DotNetInstaller.exe file, no dice.
So much for Ndiswrapper.

Maybe someone has the time and interest in downloading the driver and utility program from corega just to make sure I didn't miss something on the cabextract.

Next I took a look at the iKernel.rgs file as it is a plain text document and it looks to me as if this might be an inf, but its using the objectps.dll as a sys file and making all the changes at the registry level of windows. 
Hmmm???

Does anybody know anything about this type of situation?  
Could you explain it to me?  
Maybe my assumptions are all wrong, but at this point I am very interested in knowing how the driver is installed, and what else is going on. 
Please Ubuntu Community HELP!!!

So next I use wine on the original Setup.exe file downloaded from corega site and I get this;

fixmele:ITypeInfo_fnRelease destroy child objects
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
errle:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixmele:NdrClearOutParameters (0x7e017030,0x13f4212,0x7e017164): stub
fixme:win:SetWindowTextA setting text "corega Wireless Adapter Setup" of other process window (nil) should not use SendMessage
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:module:import_dll Library MFC42u.DLL (which is needed by L"C:\\Program Files\\corega\\CG-WLUSB2GO\\Installer\\WIN2K\\AegisI5.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\corega\\CG-WLUSB2GO\\Installer\\WIN2K\\AegisI5.exe" failed, status c0000135
wine: Call from 0x7ee962d0 to unimplemented function cfgmgr32.dll.CM_Locate_DevNodeA, aborting
fixme:shell:IShellLinkA_fnGetPath (0x16c38e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x16c38e0): WIN32_FIND_DATA is not yet filled.
err:module:import_dll Library WinSCard.dll (which is needed by L"C:\\Program Files\\corega\\CG-WLUSB2GO\\Installer\\WIN2K\\AegisE5.dll") not found
err:module:import_dll Library AegisE5.dll (which is needed by L"C:\\Program Files\\corega\\CG-WLUSB2GO\\Installer\\WIN2K\\RaUI.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\corega\\CG-WLUSB2GO\\Installer\\WIN2K\\RaUI.exe" failed, status c0000135
fixme:advapi:GetFileSecurityW (L"c:\\Program Files\\InstallShield Installation Information\\{E91E8912-769D-42F0-8408-0E329443BABC}\\") : returns fake SECURITY_DESCRIPTOR
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
errle:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be

For me this is for the most part a bunch of gobble-dee-gook, but two things I noticed.  One is that it tries to run AegisI5.exe and the other it tries to run RaUI.exe along with a lot of native windows dll (s).

AegisI5.exe can function as a loader for:\ralink\rt2500 usb wireless lan card\installer\winxp\ Among other things...

RaUI.exe as a loader for: \ralink\rt6x wireless lan card\installer\winxp\

Is there hope??
Can I somehow piggy back these drivers to make my adapter work?
I have no idea. Does anyone have any suggestions as to what my next step might be??
Is there anyone out there in the forums, in the linux community, who has any suggestions?

Please somebody HELP me!
I would appreciate it.
Thanks a bunch!
twlikes

---

### Post by twlikes on 2007-02-20
OK
I have been able to install a driver that seems to be working.  Check out this link;

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29)

The rt73 seems to recognize the equipment.  Oh by the way if you have to do the above for your adapter, the part where you have to use the uname -r command I had to input it manually.  No bigs, just type in uname -r on its own hit return and then use the number in place of the command in the instructions.

Next problem.
My adapter is seen by Network Manager and the other wifi programs I have installed, but its not connecting.  I have set the proper ESSID and WEP key (sorry can't run it open have other computers use AP) , and Kwifimanager sees signal strength and all that. 
So what's going on?
Any suggestions?
I know I'll get back to myself in a little bit, once I've figured it out.
Got love this helpful Ubuntu community.
Oh and if your wondering why I'm even bothering to post,  when I (or you for that matter) upgrade to the next version of you bummed too, we will probably have to do this all over again.
Thanks for all your help
twlikes

---

### Post by twlikes on 2007-02-21
I'm happy to report that I am sending this message on my newly reestablished wireless connection in linux.  The corega WLUSB2GO 54M wireless USB adapter with Atheros chipset  will work with Edgy.  Follow the instructions on the link in my second post, but watch out there are some commands where you need to input sudo at the beginning.  And another thing make sure you are not using a shared key, you have to have it set to open system.  Happy trails and  thanx for all the help.
twlikes

---

### Post by twlikes on 2007-03-07
I'm back.  
I'm very happy I took the time to put this process down.
I have to do it again.
I'm making my system dual-boot with windoze.
I haven't giving up on Ubuntu, but there is a lot to learn and its going to take some time.
I still would like to know where the corega drivers are hiding?
Does anyone know what's happening there?
twlikes

---

