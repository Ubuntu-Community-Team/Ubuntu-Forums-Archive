---
title: "Cannot install Flash on new install. Have googled extensively."
date: 2010-05-07
forum: New to Ubuntu
---

### Post by wcgortel on 2010-05-07
Hi all and thanks for any help in advance -

I've recently upgraded to 10.04 via a clean wipe of my prior system, and I can't seem to reinstall flash. 

I am trying to complete the process described [here]("http://www.psychocats.net/ubuntu/flash") but i get this error after APT has downloaded the files 

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


When I do, this happens interminably:

> --2010-05-07 21:30:04--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:30:25--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:30:46--  [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:31:07--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:31:28--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:31:49--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:32:11--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:32:32--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:32:53--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-07 21:33:14--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:33:57--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:34:19--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:34:40--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:35:01--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:35:24--  [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:35:45--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:36:06--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:36:27--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:36:48--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:37:09--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:37:30--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-07 21:37:51--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:38:33--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:38:54--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving voxel.dl.sourceforge.net... 74.63.52.167, 74.63.52.168, 74.63.52.169, ...
Connecting to voxel.dl.sourceforge.net|74.63.52.167|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.168|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.169|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|69.9.191.18|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|69.9.191.19|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.162|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.163|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:41:24--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:41:45--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:42:06--  [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:42:27--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:42:48--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:43:09--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:43:30--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:43:51--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:44:12--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-07 21:44:33--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:45:16--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:45:37--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving voxel.dl.sourceforge.net... 74.63.52.163, 74.63.52.167, 74.63.52.168, ...
Connecting to voxel.dl.sourceforge.net|74.63.52.163|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.167|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.168|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.169|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|69.9.191.18|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|69.9.191.19|:80... failed: Connection timed out.
Connecting to voxel.dl.sourceforge.net|74.63.52.162|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:48:05--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:48:26--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:48:47--  [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:49:08--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:49:29--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:49:50--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:50:11--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:50:33--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:50:54--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-07 21:51:15--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving ufpr.dl.sourceforge.net... 200.17.202.1, 200.236.31.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:51:58--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:52:19--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:52:42--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:53:03--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:53:24--  [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:53:45--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:54:06--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:54:28--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:54:49--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:55:10--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:55:31--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... failed: Connection timed out.
Connecting to nchc.dl.sourceforge.net|2001:e10:ffff:1f02::17|:80... failed: Network is unreachable.
--2010-05-07 21:55:52--  [http://ufpr.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://ufpr.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving ufpr.dl.sourceforge.net... 200.236.31.1, 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.236.31.1|:80... failed: Connection timed out.
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:56:34--  [http://internode.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://internode.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving internode.dl.sourceforge.net... 150.101.135.12
Connecting to internode.dl.sourceforge.net|150.101.135.12|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:56:55--  [http://voxel.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://voxel.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving voxel.dl.sourceforge.net... 72.26.192.194
Connecting to voxel.dl.sourceforge.net|72.26.192.194|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:57:19--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:57:40--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:58:01--  [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:58:22--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving switch.dl.sourceforge.net... 130.59.138.21, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable.
--2010-05-07 21:58:43--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:59:04--  [http://dfn.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://dfn.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving dfn.dl.sourceforge.net... 194.95.236.130
Connecting to dfn.dl.sourceforge.net|194.95.236.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 21:59:25--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving heanet.dl.sourceforge.net... 193.1.193.66, 2001:770:18:aa40::c101:c142
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Connecting to heanet.dl.sourceforge.net|2001:770:18:aa40::c101:c142|:80... failed: Network is unreachable.
--2010-05-07 21:59:46--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... failed: Connection timed out.
Giving up.

--2010-05-07 22:00:07--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
Resolving nchc.dl.sourceforge.net... 211.79.60.17, 2001:e10:ffff:1f02::17


I would greatly appreciate any ideas. I am able to apt-get things from the terminal and also to download this particular file from any of these websites.

Thanks very much -

Will. 

info:

here is LSPCI for my computer
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by ubunterooster on 2010-05-07
64-bit ubuntu or 32-bit?
type uname -a into terminal if unsure

---

### Post by lkraemer on 2010-05-07
Why not just enable the Partner Repo, in SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES, then run Synaptics and select Adobe Flash to be installed?

lk

---

### Post by ubunterooster on 2010-05-07
If 64-bit use the following link 


[64-bit flash]("http://ubuntuforums.org/showthread.php?t=1358591")

---

### Post by bark50 on 2010-05-07
Or go here -> [http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595") for a little utility that will delete and install 32-bit or 64-bit flash.

---

