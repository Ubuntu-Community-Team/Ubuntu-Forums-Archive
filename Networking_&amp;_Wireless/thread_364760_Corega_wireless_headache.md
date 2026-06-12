---
title: "Corega wireless headache"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by twlikes on 2007-02-18
Hello Everyone
I'm hoping someone knows a way to fix my wireless problem, let me explain.  I have a corega 54M wireless USB adapter, using an Atheros chipset.  The CD that came with it does not have a driver file, it is somehow contained in the installation app.  There does not seem to be a cab file on the CD either.  The corega website has an updated driver download, but that also comes in the form of an executable.  I have read and tried to implement other suggested solutions dealing with this chipset, but to no avail.  And if you haven't already guessed I'm new to Ubuntu without alot of know how.  Does anyone have any suggestions, I would appreciate it.
Thanks a bunch!
twlikes

---

### Post by twlikes on 2007-02-20
OK
Let me explain a little more.  

I'm running Edgy.

I was able to cabextract a data1.cab file that came with the product on installation CD.  Got a lot of junk and no .sys or .inf files,

So I downloaded the updated driver and utility exe from the corega website.

[http://www.corega.com.tw/support/download/files/driver/WLUSB2GO_Windows.zip](http://www.corega.com.tw/support/download/files/driver/WLUSB2GO_Windows.zip)

Then I use cabextract again on the downloaded Setup.exe file and I get this list of files;

ctor.dll            
IKernel.dll 
IScript.dll  
ISProBENT.tlb 
objectps.dll
DotNetInstaller.exe 
iKernel.rgs 
ISProBE9x.tlb 
IUser.dll

NO sys or inf files? 
What gives??
I try to do a cabextract/unshield on the DotNetInstaller.exe file, no dice.

I take a look at the iKernel.rgs file as it is a plain text document and it looks to me as if this might be an inf, but its using the objectps.dll as a sys file and making all the changes at the registry level of windows.  So much for Ndiswrapper.
Hmmm???

Anybody with a lot of know how feel like explaining it to me, maybe I have this all wrong, but at this point I would like to know what's going on.  Please Ubuntu Community?

So next I wine the original Setup.exe file downloaded from corega site and I get this;

fixme:ole:ITypeInfo_fnRelease destroy child objects
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
err:storage:Storage32Impl_SmallBlocksToBigBlocks conversion failed: resRead = 0x8003001e, resWrite = 0x00000000
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
err:ole:get_unmarshaler_from_stream Failed to read common OBJREF header, 0x00000001
fixme:ole:NdrClearOutParameters (0x7e017030,0x13f4212,0x7e017164): stub
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
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be
err:ole:dispatch_rpc no apartment found for ipid {ffffffff-ffff-ffff-1000-00000a000000}
err:rpc:I_RpcReceive we got fault packet with status 0x6be

Now I know this is for the most part a bunch of gobble-dee-gook, but two things I noticed, and maybe just because they weren't gobble-dee-gook to me.  One is that it tries to run AegisI5.exe and the othe it tries to run RaUI.exe along with a lot of native windows dll (s).

AegisI5.exe can function as a loader for:\ralink\rt2500 usb wireless lan card\installer\winxp\   Among other things...

RaUI.exe as a loader for: \ralink\rt6x wireless lan card\installer\winxp\

So once again is there anyone out there in the forums, in the linux community, who has any suggestions as to what my next step might be??

Maybe someone would like to download the driver and utility program from corega just to make sure I didn't miss something on the cabextract.

Please somebody talk to me. HELP!

---

