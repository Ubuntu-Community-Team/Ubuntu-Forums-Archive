---
title: "Connecting to Residence Hall printer"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by sixblades on 2008-11-13
So, at my college there's a network that all residents in the dorms can use called "ResNet" (creative, no?). At each hall there's typically a printer at the front desk that can be sent jobs from any computer on the network. I dual boot but I live in linux, vista is only for games + music production and I rarely use it, so I know that it works in Vista. The network home page has a link to a VB script (I'm assuming that's what it is...) that windows users can download that will configure their connection to the printer in their residence hall.

I thought I might be able to figure out what the script's doing so I opened it up in gedit and found this line of code:
```
	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\ana", False, strUser, strPass
```

I noticed the samba address so I pointed nautilus to:
```
smb://printer/ana
```

At this point nautilus asked me to enter my username and password to access the share. And that's as far as I got.

I know for sure that my username and password are correct, but I can't figure out for the life of me why I can't connect.

Can anyone help me out? It doesn't seem like anything too specialized is going on here, but maybe I don't know enough.

Here's the entire VB script:
```

Set wshNetwork = CreateObject("Wscript.Network")

Set objShell = CreateObject("WScript.Shell")



' Get the users Perm number

Do

resultPerm = InputBox("Enter your perm number", "ResNet Printer Script")

If resultPerm <> "" Then

	permInput = True

End If

Loop until permInput = True



' Get the users password

Do

resultPass = InputBox("Enter your ResNet password", "ResNet Printer Script")

If resultPass <> "" Then

	passInput = True

End If

Loop until passInput = True



'Edit the variables

strUser = "rc\" & resultPerm

strPass = resultPass



' Create the prompt for the printer

strPrompt = "Please select a printer from the list below " _

	  & Vbcrlf _

	  & "and type the corresponding queue name into " _

	  & Vbcrlf _

	  & "the prompt" _

	  & Vbcrlf _

	  & Vbcrlf _

	  & "Location		-	Queue" _

	  & Vbcrlf _

	  & Vbcrlf _

	  & "Anacapa		-	ana" _

	  & Vbcrlf _

	  & "Manzanita Village	-	mz" _

	  & Vbcrlf _

	  & "San Miguel		-	sm" _

	  & Vbcrlf _

	  & "San Nicholas		-	sn" _

	  & Vbcrlf _

	  & "San Rafael		-	srt" _

	  & Vbcrlf _

	  & "Santa Cruz		-	sc" _

	  & Vbcrlf _

	  & "Santa Rosa		-	sr" _

	  & Vbcrlf _

	  & "Santa Catalina, North	-	sct-n" _

	  & Vbcrlf _

	  & "Santa Catalina, South	-	sct-s"



' As the user for the queue, and sanitize

Do

resultPrinter = InputBox(strPrompt, "ResNet Printer Script")

If resultPrinter = "ana" Or resultPrinter = "mz" _

Or resultPrinter = "sm" Or resultPrinter = "sn" _

Or resultPrinter = "srt" Or resultPrinter = "sc" _

Or resultPrinter = "sr" Or resultPrinter = "sct-n" _

Or resultPrinter = "sct-s" Then

	passPrinter = True

End If

Loop until passPrinter = True



' Remove the old port if it's taken

Set oPrinters = wshNetwork.EnumPrinterConnections

For i = 0 to oPrinters.Count - 1 Step 2

	If oPrinters.Item(i) = "LPT3" Then

		' Free up my LTP port!

		wshNetwork.RemovePrinterConnection oPrinters.Item(i), true, true

	End If

Next



' Remove the old printer since we can only have one

Set iPrinters = GetObject("winmgmts:").instancesof ("win32_printer")

for each print in iPrinters

	If print.name = "Anacapa" Or print.name = "Manzanita Village" _

	Or print.name = "San Miguel" Or print.name = "San Nicholas" _

	Or print.name = "San Rafael" Or print.name = "Santa Cruz"_

	Or print.name = "Santa Rosa" Or print.name = "Santa Catalina - North" _

	Or print.name = "Santa Catalina - South" Then

		print.Delete_

	End If

next



' Work the magic

Select Case resultPrinter

Case "ana"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\ana", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Anacapa"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "mz"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\mz", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Manzanita Village"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sm"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sm", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""San Miguel"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sn"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sn", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""San Nicholas"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "srt"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\srt", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""San Rafael"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sc"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sc", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Santa Cruz"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sr"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sr", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Santa Rosa"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sct-n"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sct-n", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Santa Catalina - North"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""



Case "sct-s"

	' Create the new printer connection

	wshNetwork.AddPrinterConnection "LPT3:", "\\printer\sct-s", False, strUser, strPass



	' Add the printer to the system

	objShell.run "rundll32 printui.dll,PrintUIEntry /if /b ""Santa Catalina - South"" /r ""LPT3:"" /m ""HP Laserjet 4250 PCL 5"""

End Select



WScript.sleep 6000



WScript.Echo "Your Printer has been sucessfully Installed, It may take a moment for the printer to appear in your system"

```

---

### Post by sixblades on 2008-11-17
*Bump* Come on yall!

---

