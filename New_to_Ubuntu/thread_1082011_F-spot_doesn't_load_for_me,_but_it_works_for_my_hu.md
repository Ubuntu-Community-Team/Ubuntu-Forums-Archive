---
title: "F-spot doesn't load for me, but it works for my husband!"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-02-27
Hi,

We only installed Ubuntu 8.04 as a dual-boot on our PC a couple of weeks ago.  My husband was impressed by how much easier it was to download photos from his camera using F-spot than with his usual XP app.  I tried this for the first time a couple of days ago, and it won't work for me.  The camera is recognised, and I get a dialog box asking if I want to download the pictures.  Then the "starting F-spot" box appears in the bottom panel and after a few seconds disappears.  Nothing else happens.  I've tried opening F-spot without the camera connected, but the same thing happens.  I've re-installed F-spot, but no change.  It's still working fine for my husband, on a different user account on the same computer, with an identical camera.

Does anyone have any suggestions, as I'm completely bewildered.

Thanks.

Lesley

---

### Post by Ms_Angel_D on 2009-02-27
To be honest with you I probably can't help you but I can give you a head start the person who can help you will probably want you to open the terminal (Programs->Accessories->Terminal) type f-spot then post the output here, it will save you lot's of time in getting your error fixed ;)

Angel

---

### Post by Bearly Able on 2009-02-27
Thanks for the tip!  Here's the output:
```

Starting new FSpot server
XXXXX
Mono.Data.SqliteClient.SqliteSyntaxException: no such table: tags
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Data.SqliteClient.SqliteCommand:ExecuteReader ()
  at Banshee.Database.QueuedSqliteCommand.Execute () [0x00000] 
XXXXX
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Starting new FSpot server
Can't get a connection to the dbus. Trying again...
Sorry, couldn't start F-Spot

```

---

### Post by nothingspecial on 2009-02-27
See [COLOR="Red"][here]("http://ubuntuforums.org/showthread.php?t=525632")[/COLOR]

To see any folder that starts with a . you need to press Ctrl + H.
Do what it says, copy the folder somewhere so you can put it back again if this doesn`t work, before you delete it.

Don`t worry f-spot will create a new one next time you start it and if it doesn`t for any reason you`ve got a backup.

---

### Post by Bearly Able on 2009-02-27
Thanks, nothingspecial, that's done the trick.

---

