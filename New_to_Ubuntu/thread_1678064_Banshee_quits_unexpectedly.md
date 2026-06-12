---
title: "Banshee quits unexpectedly"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by slgtheindividual on 2011-01-29
I'm using latest kernel and latest ubuntu release, 32-bit, I have all  the restricted extras installed and have updated everything. The problem  is that when I push the next track button in banshee or when it gets to the end of a track banshee  unexpectedly quits, however rhythmbox works fine. Thank you in advance  for any assistance, if there is any further information required please  feel free to ask.

---

### Post by TeoBigusGeekus on 2011-01-29
Launch banshee from terminal and see if you get any error messages in it when it crashes.

---

### Post by NightwishFan on 2011-01-29
Just to clarify the command is banshee or banshee-1.

---

### Post by slgtheindividual on 2011-02-08
When I launch Banshee from the terminal I get the following output


~$ banshee

"
[Info  16:57:11.759] Running Banshee 1.8.1: [Ubuntu 10.10 (linux-gnu, i686) @ 2011-02-02 09:04:16 UTC]
[Warn  16:57:12.739] Error determining if ANALYZE is necessary - Mono.Data.Sqlite.SqliteException: The database disk image is malformed
database disk image is malformed (in `Mono.Data.Sqlite')
  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] in <filename unknown>:0 
[Info  16:57:12.745] Starting collection of anonymous usage data
[Info  16:57:14.179] Updating web proxy from GConf
[Info  16:57:14.246] All services are started 2.085356
[Info  16:57:17.401] nereid Client Started
[Info  16:57:17.722] AppleDeviceSource is ignoring unmounted volume OS
[Warn  16:57:17.723] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
bpm_detect got error: Your GStreamer installation is missing a plug-in. gstdecodebin2.c(3076): gst_decode_bin_expose (): /GstPipeline:pipeline/GstDecodeBin2:decodebin2:
no suitable plugins found
bpm_detect got error: Your GStreamer installation is missing a plug-in. gstdecodebin2.c(3076): gst_decode_bin_expose (): /GstPipeline:pipeline/GstDecodeBin2:decodebin2:
no suitable plugins found
bpm_detect got error: Internal data flow error. gstbasesrc.c(2550): gst_base_src_loop (): /GstPipeline:pipeline/GstFileSrc:filesrc:
streaming task paused, reason not-linked (-1)
 4.1392180919647

[Info  16:57:31.587] Posted usage data? True
[Info  16:58:17.026] Uncached artwork size 175 requested
[Info  16:58:17.064] Uncached artwork size 38 requested

Unhandled Exception: Mono.Data.Sqlite.SqliteException: Sqlite error
cannot start a transaction within a transaction
  at Mono.Data.Sqlite.Sqlite3.Reset (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement stmt) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteCommand.ExecuteNonQuery () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand:ExecuteNonQuery ()
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] in <filename unknown>:0 
"

Thank you in advance

---

### Post by NightwishFan on 2011-02-08
Try this, open your home folder, hit CTRL+H to show hidden files. Browse to .config. Rename the folder "banshee-1" to banshee-1-backup". Then try to start Banshee.

---

### Post by slgtheindividual on 2011-02-08
> **NightwishFan said:**
> Try this, open your home folder, hit CTRL+H to show hidden files. Browse to .config. Rename the folder "banshee-1" to banshee-1-backup". Then try to start Banshee.

That seems to have worked perfectly and solved the problem, thank you very much.

Could you tell me what difference it made by renaming that folder?

Thank you again.

---

### Post by NightwishFan on 2011-02-08
It seems banshee somehow had it's database corrupted during its use. This simply reset it. As for what caused the corrution, abrupt machine power loss?

---

### Post by slgtheindividual on 2011-02-08
That could well be it. Would it be ok to delete the backup now? (a new file with the old name "banshee-1" automatically appeared when I started banshee up again)

Thank you again, you've been very helpful.

---

### Post by NightwishFan on 2011-02-08
Yes, you can delete it. No problems, enjoy! :)

---

