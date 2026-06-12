---
title: "how to upgrade ubuntu 8.04 to higher version"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by becoolpal on 2009-07-01
i am using ubuntu 8.04 (hardy)
i want it to  upgrade it to higher version.How can i do it

---

### Post by HotShotDJ on 2009-07-01
> **becoolpal said:**
> i am using ubuntu 8.04 (hardy)
i want it to  upgrade it to higher version.How can i do it

[LIST]
[*]System --> Administration --> Software Sources
[*]Click Updates tab
[*]Find "Release upgrade" and select your preference in the drop-down menu (normal release, long-term support releases only, or never)
[*]If you select "normal releases," your update manager should now ask you if you want to update.  Simply say "yes" and the update manager will take care of it for you.
[/LIST]

NOTE:  Be sure to read the release notes for the version you are upgrading to (for example, see [Jaunty Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/904")) or you will risk being bitten by bugs, depending on your particular hardware.  This is true any time you perform major upgrades.

---

### Post by ivanvajar on 2009-07-01
It's important that you read release notes. Kernel updates may mess your hardware drivers up. One of the solutions is to disable proprietary drivers and enable them after upgrade.

---

### Post by becoolpal on 2009-07-01
> **ivanvajar said:**
> It's important that you read release notes. Kernel updates may mess your hardware drivers up. One of the solutions is to disable proprietary drivers and enable them after upgrade.


@ [ivanvajar]("http://ubuntuforums.org/member.php?u=755964") :
how should i disable proprietary drivers before upgrading?

---

### Post by LowSky on 2009-07-01
system > admin > proprietart drivers, turn them off.

You might not have any running if you dont use wifi or a graphics card from nvidia or ati

---

### Post by becoolpal on 2009-07-01
thanx a lot mate!!!

---

