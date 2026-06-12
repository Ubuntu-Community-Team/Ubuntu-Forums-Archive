---
title: "I need some advice with NXServer (nomachine)"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by jpgauthier on 2007-12-11
Hello,

I need some help with my nxserver setup. So far, i have downloaded and installed the debian pkg from nomachine website and installed in the followed order : client, node, server using the dpkg -i shell command. 

My /usr/NX/etc/server.cfg look like this (its pretty much the default config) :

```

#
# Set config file format version.
#
ConfigFileVersion = "2.0"

#
# Set the log level of NX Server. NX server logs to the syslog all
# the events that are <= to the level specified below, according to
# the following convention:
#
# KERN_ERR         3: Error condition.
# KERN_INFO        6: Informational.
# KERN_DEBUG       7: Debug-level messages.
#
# Note, anyway, that NX server uses level 6 in the syslog to log the
# event. This is intended to override any setting on the local syslog
# configuration that would prevent the event from being actually logged.
#
# The suggested values are:
#
# 6: This is the default value. Only the important events
#    are logged.
#
# 7: Sets logs to level debug.
#
SessionLogLevel = "6"

#
# Specify hostname for the NX server.
#
ServerName = ""

#
# Specify the TCP port where the NX server SSHD daemon is running.
#
SSHDPort = "22"

#
# Set the base display number for NX sessions.
#
DisplayBase = "1000"

#
# Set the maximum number of displays reserved for NX sessions.
#
DisplayLimit = "200"

#
# Set the maximum number of concurrent NX sessions.
#
SessionLimit = "20"

#
# Set the maximum number of concurrent NX sessions that can be run by
# a single user. By default a user can run as many sessions as they
# are allowed on the server. By setting this value to 1, the system
# administrator can force the user to terminate any suspended session
# before starting a new one.
#
SessionUserLimit = "20"

#
# Set for how long NX server will retain data related to terminated
# sessions in its session history.
#
# <0: Never delete data from NX session history.
#
#  0: Disable NX sessions history.
#
# >0: Keep data in session history for this amount
#     of seconds.
#
# The default value, 2592000, lets NX server keep session data
# for 30 days.
#
SessionHistory = "2592000"

#
# Allow the server to terminate oldest suspended sessions:
#
# 1: Enabled. Enable the automatic kill of the suspended
#    sessions.
#
# 0: Disabled. Suspended sessions are never terminated.
#
# When this option is set, and the server capacity has been reached,
# i.e. the maximum number of concurrent sessions could be exceeded,
# the server will kill the oldest suspended sessions to make room for
# the new user.
#
EnableAutokillSessions = "0"

#
# Enable persistent sessions for users. If the option is followed by
# the keyword 'all', all users are allowed to run persistent sessions.
# Alternatively, it can be followed by a list of comma-separated user-
# names. The default value is 'all' which corresponds to enabling
# persistent sessions for all users. Values specified are overriden
# by the value set for the 'DisablePersistentSession' key.
#
EnablePersistentSession = "all"

#
# Disable persistent sessions for users. If the option is followed by
# the keyword 'all', no user is allowed to run persistent sessions. Al-
# ternatively, the option can be followed by a list of comma-separated
# usernames. The default value is the empty string which corresponds
# to disabling persistent sessions for no user. The values specified
# override the values set for the 'EnablePersistentSession' key.
#
DisablePersistentSession = ""

#
# Enable or disable SSL encryption of all traffic.
#
#
# 1: Enabled. Unencrypted connections between the proxies will
#    be allowed.                                      
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    server will force the client to tunnel the proxy
#    connections over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if subsequent communication must
# take place through a direct connection between the proxies or by
# tunneling it through SSH. You may uncomment the following line
# and set the value to 0 to increase the security of the host
# server or if your NX server is behind a firewall preventing
# the access to the set of ports used by the NX server.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DisplayBase + 4000
#
# to:
#
# DisplayBase + 4000 + DisplayLimit
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the
# same LAN or when performance is an issue.
#
EnableUnencryptedSession = "1"

#
# Enable or disable support for user profiles:
#
# 1: Enabled. The NX server allows the NX session to start
#    according to the set of rules specified for the system
#    or on a per-user basis.
#
# 0: Disabled. The NX server starts the session without apply-
#    ing any rules.
#
# The administrator can configure access to applications and nodes
# by creating a specific profile for the NX system, which will be
# applied to any user starting a session on this server, or by def-
# ining profiles on a per-user basis. Any profile consists of a set
# of rules specifying what the user can or can't do in the session.
#
EnableUserProfile = "0"

#
# Enable or disable clipboard:
#
# client: The content copied on the client can be pasted inside the
#         NX session.
#
# server: The content copied inside the NX session can be pasted
#         on the client.
#
# both:   The copy&paste operations are allowed between both the
#         client and the NX session and viceversa.
#
# none:   The copy&paste operations between the client and the NX
#         session are never allowed.
#
EnableClipboard = "both"

#
# Enable or disable NX users DB:
#
# 1: Enabled. Only users listed in NX users DB can login to the NX
#    server.
#
# 0: Disabled. All the authenticated users can login.
#
# If the NX user DB is disabled, any user providing a valid password
# from local DB or through SSHD authentication, can connect to the NX
# system. This is likely to be the default when SSHD authentication
# with PAM is enabled.
#
EnableUserDB = "0"

#
# Enable or disable NX password DB:
#
# 1: Enabled. Use NX password DB to authenticate users.
#
# 0: Disabled. Use SSHD + PAM authentication.
#
# System administrators can enable a restricted set of users to con-
# nect to the NX server by setting EnableUserDB to 1 and adding
# those users to the DB. If user is enabled to connect, his/her pass-
# word will be verified against the current PAM settings by the SSHD
# daemon.
#
# If both 'EnableUserDB' and 'EnablePasswordDB' are set to 0, any
# user being authenticated by SSHD account will be enabled to connect
# to the system.
#
EnablePasswordDB = "0"

#
# Specify hostname of the server used for NX SSH authentication.
#
SSHDAuthServer = ""

#
# Specify the TCP port where the SSHD daemon is running on the NX SSH
# authentication server.
#
SSHDAuthPort = "22"

#
# Enable or disable statistics:
#
# 1: Enabled. Enable the production of NX statistics.
#
# 0: Disabled. Disable the production of NX statistics.
# 
# Run the nxstat daemon in background. This daemon can be used to
# produce statistics about the NX services and the node host machine
# either for localhost and any of the available nodes when the load
# balancing is enabled. This requires that the nxsensor daemon is
# started on each of the node machines.
#
EnableStatistics = "0"

#
# Specify the port where the server will contact the nxsensor daemons
# to collect the statistics.
#
ServerSensorPort = "19250"

#
# Enable or disable load balancing:
#
# 1: Enabled. Let  NX server decide the node host according to the
#    hosts available in the NX Node DB.
#
# 0: Disabled. Start NX session on localhost.
#
EnableLoadBalancing = "0"

#
# Set for how long the NX server daemon has to wait for a reply from
# the node machine before considering that this host is unreachable.
# The default value, 10, let NX server daemon to wait for 10 seconds.
#
NodeResponseTimeout = "10"

#
# Enable or disable monitoring the NX Node host machines when load-
# balancing is enabled in the NX Advanced Server configuration.
#
# 1: Enabled. Enable starting of the NX Server daemon.
#
# 0: Disabled. Disable starting of the NX Server daemon.
#
EnableNodeMonitoring = "0"

#
# Specify a list of comma-separated 'hostname:port' values for XDM
# server.
#
RoundRobinXdmList = "localhost:177"

#
# Enable or disable the XDM round robin query:
#
# 1: Enabled. Let NX server decide XDM host according to hostnames
#    that are defined in the RoundRobinXdmList key.
#
# 0: Disabled.
#
EnableRoundRobinXdmQuery = "1"

#
# Enable or disable the XDM indirect query:
#
# 1: Enabled. Let the user obtain a list of available XDM hosts.
#
# 0: Disabled.
#
EnableIndirectXdmQuery = "0"

#
# Enable or disable the XDM direct query:
#
# 1: Enabled. Let client specify XDM host.
#
# 0: Disabled.
#
EnableDirectXdmQuery = "0"

#
# Enable or disable the XDM broadcast query:
#
# 1: Enabled. Let client connect to the first responding XDM host.
#
# 0: Disabled.
#
EnableBroadcastXdmQuery = "0"

#
# Specify path and name of the command 'sessreg'.
#
CommandSessreg = "/usr/X11R6/bin/sessreg"

#
# Specify the location and file name of the SSH authorized keys.
#
SSHAuthorizedKeys = "authorized_keys2"

#
# Accept or refuse the NX client connection if SSHD does not export
# the 'SSH_CONNECTION' and 'SSH_CLIENT' variables in the environment
# passed to the NX server.
#
# 1: Refuse. Check the remote IP and don't accept the connection
#    if it can't be determined.
#
# 0: Accept. Check the remote IP and accept the connection even if
#    the remote IP is not provided.
#
SSHDCheckIP = "0"

#
# Enable or disable support for automatic provision of NX guest users:
#
# 1: Enabled. The NX server creates system accounts for guest users.
#
# 0: Disabled.
#
EnableGuestUser = "0"

#
# Specify the base username to be used by NX server to create guest
# users accounts. The server will add a progressive number to the
# name specified by GuestName, according to the range of values set
# in the BaseGuestUserId and GuestUserIdLimit keys.
#
GuestName = "guest"

#
# Set the base User Identifier (UID) number for NX guest users.
#
BaseGuestUserId = "10"

#
# Set the maximum User Identifier (UID) number reserved for NX guest
# users.
#
GuestUserIdLimit = "200"

#
# Set the Group Identifier (GID) for NX guest users. The specified
# GID must already exist on the system.
#
GuestUserGroup = "guest"

#
# Set the maximum number of concurrent NX guest users.
#
GuestUserLimit = "10"

#
# Set the maximum number of NX sessions a NX guest user can run before
# his/her account is terminated.
#
GuestUserConnectionLimit = "5"

#
# Set for how long the NX server has to retain NX guest users accounts.
#
#  0: NX guest users accounts are never removed.
#
# >0: Maintain NX guest users accounts for this amount
#     of seconds.
#
# The default value, 2592000, lets NX server keep guest users accounts
# for 30 days.
#
GuestUserAccountExpiry = "2592000"

#
# Set for how long the NX server has to keep alive a NX guest user's
# session. When the time is expired, NX server will kill the session.
#
#  0: NX guest user's session is never terminated.
#
# >0: Keep alive NX guest user' session for this amount
#     of seconds.
#
GuestConnectionExpiry = "0"

#
# Enable or disable possibility for NX guest users to suspend sessions:
#
# 1: Enabled. The NX server lets NX guest users suspend sessions.
#
# 0: Disabled.
#
GuestUserAllowSuspend = "1"

#
# Set the home directory for NX guest users. If an empty value is
# specified, the NX server will create the guest user's home in the
# default directory set on the system. 
#
GuestUserHome = "/home"

#
# Enable or disable removing the guest user from the system when the
# account is expired:
#
# 1: Enabled. When the guest account is expired, the NX server will
#    delete the account from both the system and the NX guests DB
#    and will remove the home directory.
#
# 0: Disabled. When the guest account is expired, the NX server will
#    keep the guest account on the system but will forbid this user
#    to start new sessions on the server.
#
EnableGuestWipeout = "1"

#
# Allow the server to set disk quota for the guest accounts:
#
# 1: Enabled. When a new guest account is created on the system,
#    the server will set the disk quota for this user.
#
# 0: Disabled. No restrictions on the amount of disk space used
#    by each guest user are applied.
#
EnableGuestQuota = "0"

#
# Specify the username of the account to be used as a protoype for
# propagating its disk quota settings to all the new guest accounts.
# If the softlimit or the hardlimit on either the inode or the disk
# block are set, they will override the settings applied to the user
# prototype.
#
GuestQuotaProtoname = "protoguest"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of inodes. This limit can be exceeded
# for the grace period.
#
GuestQuotaInodeSoftlimit = "0"

#
# Specify the absolute maximum amount of disk space available for
# each of the guest users, checked as number of inodes. Once this
# limit is reached, no further disk space can be used.
#
GuestQuotaInodeHardlimit = "0"

#
# Specify the maximum amount of disk space available for each of the
# guest users, checked as number of disk blocks consumed. This limit
# can be exceeded for the grace period.
#
GuestQuotaBlockSoftlimit = "0"

#
# Specify the absolute maximum amount of disk space available for each
# of the guest users, checked as number of disk blocks consumed. Once
# this limit is reached, no further disk space can be used.
#
GuestQuotaBlockHardlimit = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GuestQuotaInodeSoftlimit key may be
# exceeded.
#
GuestQuotaInodeGracePeriod = "0"

#
# Specify the grace period, expressed in seconds, during which the
# soft limit, set in the GuestQuotaBlockSoftlimit key may be
# exceeded.
#
GuestQuotaBlockGracePeriod = "0"

#
# Specify a list of comma-separated filesystem names or devices to
# which the disk quota restrictions will be applied. The default
# value is 'all' which corresponds to applying the disk quota limits
# to all the filesystems having disk quota enabled.
#
GuestQuotaFilesystems = "all"

#
# Set the User Identifier (UID) number for NX users. If an empty value
# is specified, the NX server will create the account with the default
# value set on the system.
#
UserId = "10"

#
# Set the Group Identifier (GID) for NX users. If an empty value is
# specified, the NX server will create the account with the default
# value set on the system.
#
UserGroup = "users"

#
# Set the home directory for NX users. If an empty value is specified,
# the NX server will create the user's home in the default directory
# set on the system.
#
UserHome = "/home"

#
# Allow session shadowing on this server:
#
# 1: Enabled.  Each user can require to attach to an already running
#    session. The session owner has to accept connection.
#
# 0: Disabled. Session shadowing is forbidden.
#
EnableSessionShadowing = "1"

#
# Allow session shadowing in interactive mode:
#
# 1: Enabled. User attaching to the session can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User
#    attaching to the session can't interact with the session.
#
EnableInteractiveSessionShadowing = "1"

#
# Enable or disable NX server requiring authorization to the owner
# of the NX session before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the master session before trying to share the session.
#
# 0: Disabled. NX server tries to share the NX session without
#    the need of any authorization from the owner of the master
#    desktop.
#
EnableSessionShadowingAuthorization = "1"

#
# Allow desktop sharing on this server:
#
# 1: Enabled. User can require to attach to the native display
#    of the nodes. The desktop's owner has to accept connection.
#
# 0: Disabled. Desktop sharing is forbidden.
#
EnableDesktopSharing = "1"

#
# Allow desktop sharing in interactive mode:
#
# 1: Enabled. User attaching to the desktop can interact with
#    the session.
#
# 0: Disabled. The session is shadowed in view-only mode. User
#    attaching to the desktop can't interact with the session.
#
EnableInteractiveDesktopSharing = "1"

#
# Allow the NX user to connect to a desktop owned by a user who is
# not an NX user:
#
# 1: Enabled. Allow an NX user to connect to a desktop owned
#    by a user who is not an NX user. This requires running a
#    privileged script as root and will work only if the node
#    is the same machine where NX server is running.
#
# 0: Disabled. An NX user can connect only to a desktop owned
#    by an NX user when EnableDesktopSharing is enabled.
#
EnableFullDesktopSharing = "0"

#
# Allow the NX user to connect to a desktop owned by root:
#
# 1: Enabled. Allow an NX user to connect to a desktop owned by
#    root (or Administrator on a Windows machine). This requires
#    EnableFullDesktopSharing to be enabled.
#
# 0: Disabled. A NX user is forbidden to connect to a desktop
#    owned by root.
#
EnableAdministratorDesktopSharing = "0"

#
# Enable or disable NX server requiring authorization to the owner
# of the desktop before sharing the session.
#
# 1: Enabled. NX server asks for authorization to the owner
#    of the desktop.
#
# 0: Disabled. NX server tries to share the native display
#    without the need of any authorization from the owner
#    of the desktop.
#
EnableDesktopSharingAuthorization = "1"

#
# Enable or disable NX server requiring authorization before sharing
# the session either when the X server is running as root or gdm.
#
# 1: Enabled. NX server needs authorization to proceed with
#    sharing the session.
#
# 0: Disabled. NX server tries to share the native display
#   without the need for any authorization. Sharing the
#   session is also possible when a user is not logged
#   on to the local desktop.
#
EnableSystemDesktopSharingAuthorization = "1"

#
# Specify absolute path of the custom script to be executed before
# the user logs in. The script can accept remote IP of the user's
# machine as its input.
#
# E.g. UserScriptBeforeLogin = "/tmp/nxscript/script.sh"
#
UserScriptBeforeLogin = ""

#
# Specify absolute path of the custom script to be executed after
# the user logs in. The script can accept username as its input.
#
UserScriptAfterLogin = ""

#
# Specify absolute path of the custom script to be executed before
# the session start-up. The script can accept session ID, username,
# node host and node port as its input.
#
UserScriptBeforeSessionStart = ""

#
# Specify absolute path of the custom script to be executed after the
# session start-up. The script can accept session ID, username, node
# host and node port as its input.
#
UserScriptAfterSessionStart = ""

#
# Specify absolute path of the custom script to be executed before
# the session is closed. The script can accept session ID, username,
# node host and node port as its input.
#
UserScriptBeforeSessionClose = ""

#
# Specify absolute path of the custom script to be executed after the
# session is closed. The script can accept session ID, username, node
# host and node port as its input.
#
UserScriptAfterSessionClose = ""

#
# Specify absolute path of the custom script to be executed before
# the session is reconnected. The script can accept session ID user-
# name, node host and node port as its input.
#
UserScriptBeforeSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after the
# session is reconnected. The script can accept session ID username
# node host and node port as its input.
#
UserScriptAfterSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed before
# the session is suspended. The script can accept session ID, user-
# name, node host and node port as its input.
#
UserScriptBeforeSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed after
# the session is suspended. The script can accept session ID, user-
# name, node host and node port as its input.
#
UserScriptAfterSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed before
# session failure. The script can accept session ID username, node
# host and node port as its input.
#
UserScriptBeforeSessionFailure = ""

#
# Specify absolute path of the custom script to be executed after
# session failure. The script can accept session ID username, node
# host and node port as its input.
#
UserScriptAfterSessionFailure = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server creates the new account. The script can accept username
# as its input.
#
UserScriptBeforeCreateUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has created the new account. The script can accept user-
# name as its input.
#
UserScriptAfterCreateUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server removes the account. The script can accept username as
# its input.
#
UserScriptBeforeDeleteUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has removed the account. The script can accept username
# as its input.
#
UserScriptAfterDeleteUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server disables the user. The script can accept username as its
# input.
#
UserScriptBeforeDisableUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has disabled the user. The script can accept username
# as its input.
#
UserScriptAfterDisableUser = ""

#
# Specify absolute path of the custom script to be executed before
# NX Server enables the user. The script can accept username as its
# input.
#
UserScriptBeforeEnableUser = ""

#
# Specify absolute path of the custom script to be executed after
# NX Server has enabled the user. The script can accept username
# as its input.
#
UserScriptAfterEnableUser = ""

```

My /usr/NX/etc/node.cfg is also pretty much the default :

```

#
# Set config file format version.
#
ConfigFileVersion = "2.0"

#
# Set the log level of NX node. NX node logs to the syslog all the
# events that are <= to the level specified below, according to the
# following convention:
#
# KERN_ERR         3: Error condition.
# KERN_INFO        6: Informational.
# KERN_DEBUG       7: Debug messages.
#
# Note, anyway, that NX node uses level 6 in the syslog to log the 
# event. This is intended to override any setting on the local sys-
# log configuration that would prevent the event from being actually
# logged.
#
# The suggested values are:
#
# 6: This is the default value. Only the important events
#    are logged.
#
# 7: Set the log level to debug.
#
SessionLogLevel = "6"

#
# Enable or disable the automatic clean-up of NX session directories
# at the time sessions are terminated:
#
# 1: Enabled. This is the default value.
#
# 0: Disabled. Directories are prefixed by 'T-' and left
#    for further reference.
#
SessionLogClean = "1"

#
# Enable or disable NX node to log the X client stderr.
#
# 1: Enabled. The standard error of the X clients is redirected to
#    the 'clients' file in the session directory. 
#
# 0: Disabled. The standard error of the X clients is redirected to
#    /dev/null.
#
ClientLog = "1"

#
# Set the maximum size allowed for the log of the X clients. The node
# will terminate the session if this limit is exceeded. The default 
# value is 4194304 bytes (4MB).
#
ClientLogLimit = "4194304"

#
# Set the maximum size allowed for the session log. The node will
# terminate the session if this limit is exceeded. The default value
# is 4194304 bytes (4MB).
#
SessionLogLimit = "4194304"

#
# Enable or disable SSL encryption of all traffic between server and
# node.
#
# 1: Enabled. Unencrypted connections between the server and
#    the node will be allowed.                       
#
# 0: Disabled. Forbid the use of unencrypted connections. The
#    node will force the server to tunnel the proxy connections
#    over the encrypted channel.
#
# Session negotiation always happens across an encrypted channel.
# Normally the user can specify if the subsequent communication
# must take place through a direct connection between the proxies
# or by tunneling it through SSH. You may uncomment the following
# line and set the value to 0 to increase the security of the node
# host or if NX node is behind a firewall preventing the access to
# the set of ports used by the NX node.
#
# Unencrypted sessions require that the firewall lets the proxies
# communicate over the TCP ports ranging from:
#
# DISPLAY_BASE + 4000
#
# to:
#
# DISPLAY_BASE + 4000 + DISPLAY_LIMIT
#
# By default the user is allowed to specify if a session will run
# unencrypted, for example when running the session across the same
# LAN or when performance is an issue.
#
EnableUnencryptedSession = "1"

#
# Specify path and name of the client to be run by nxnode, nxcomp
# and nxagent, for example for issuing dialog boxes and messages,
# instead of the default nxclient.
#
CommandClient = "/usr/NX/bin/nxclient"

#
# Specify path and name of the command 'fuser' to identify processes
# using files or sockets.
#
CommandFuser = "/bin/fuser"

#
# Specify path and name of the command 'lsof' to list open files.
#
CommandLsof = "/usr/sbin/lsof"

#
# Specify path and name of the command 'xauth' to edit and display
# the authorization information used when connecting to the X server.
#
CommandXauth = "xauth"

#
# Specify path and name of the command 'xdpyinfo' for displaying
# information about an X server.
#
CommandXdpyInfo = "xdpyinfo"

#
# Specify path and name of the command 'xmodmap' to edit and display
# the keyboard modifier map and keymap table.
#
CommandXmodmap = "xmodmap"

#
# Specify path and name of the command starting 'CDE'.
#
CommandStartCDE = "cdwm"

#
# Enable or disable use of 'xkbcomp' command:
#
# 1: Enabled. Use 'xkbcomp' command.
#
# 0: Disabled.
#
EnableCommandXkbComp = "1"

#
# Specify path and name of the command 'xkbcomp' to compile XKB key-
# board description.
#
CommandXkbComp = "xkbcomp"

#
# Specify location and file name of the keymap file used by 'xkbcomp'.
#
XkbCompKeymapFile = "/etc/X11/xkb/keymap/xfree86"

#
# Specify the location and file name of the SSH authorized keys.
#
SSHAuthorizedKeys = "authorized_keys2"

#
# Specify the font server to be used by NX agent. By default the NX
# agent only uses the X11 system fonts. Uncomment the following line
# to enable use of an X Font Server.
#
AgentFontServer = "unix/:7100"

#
# Specify the path of default X window system startup script.
#
DefaultXSession = "/etc/X11/xdm/Xsession"

#
# Set the default DPI of the X server to the specified value. This
# should normally not be required, but some desktop applications fail
# to set an appropriate value and fall back to 75 DPI, which is the
# value reported by default by the X server.
#
DefaultXDPI = "96"

#
# Specify the path of libraries to be added to the agents environment.
# Be sure that NX libraries are listed first.
#
AgentLibraryPath = "/usr/NX/lib"

#
# Specify the path of libraries to be added to NX proxy environment.
#
ProxyLibraryPath = "/usr/NX/lib"

#
# Specify a list of libraries to be preloaded in X applications. This key
# is only used when running sessions in single application mode without NX 
# agent encoding. Starting from version 1.5.0, the node doesn't preload the
# NX X11 libraries.
#
# The default is an empty list.
#
# ApplicationLibraryPreload = "/usr/NX/lib/libX11.so.6.2:/usr/NX/lib/libXext.so.6.4:/usr/NX/lib/libXcomp.so.1:/usr/NX/lib/libXcompext.so.1:/usr/NX/lib/libXrender.so.1.2"
#
ApplicationLibraryPreload = ""

#
# Specify a list of directories to be added to the library path of X
# clients when run inside a session in single application mode without
# NX agent encoding.
#
# The default is an empty list.
#
# ApplicationLibraryPath = "/usr/NX/lib" 
#
ApplicationLibraryPath = ""

#
# Enable or disable TCP_NODELAY setting in NX proxy.
#
# 1: Enabled. Let NX client choose whether to enable or not TCP_NODELAY
#    on proxy socket.
#
# 0: Disabled. Disable TCP_NODELAY.
#
# Due to a bug in old Linux kernels, enabling TCP_NODELAY when running
# sessions over PPP links can cause sessions to fail if a serious net-
# work congestion is encountered.
#
ProxyTCPNodelay = "0"

#
# Specify a list of comma-separated options to be added to the
# NX proxy transport. Look at the NX proxy documentation for more
# information about the available options. Options specified in 
# 'ProxyExtraOptions' override the parameters set by NX client.
#
ProxyExtraOptions = "limit=256k,link=modem"

#
# Append arguments to the command line used to run the NX agent for
# X (Unix sessions).
#
# Mutiple parameters can be specified by separating them with a blank
# character. Note that, for security reasons, no shell interpretation
# is made.
#
AgentExtraOptions = "-nocomposite -noshpix"

#
# Specify the default Window Manager to be used when running single
# applications in a virtual desktop.
#
DefaultXWM = "twm"

#
# Specify the domain of the Windows Terminal Server.
#
DefaultRDPDomain = ""

#
# Specify the path of base directory where the NX node has to mount
# shares exported by the user. The default value is $(HOME)/MyShares.
#
ShareBasePath = "$(HOME)/MyShares"

#
# Allow the node to use privileged scripts to manage the shares:
# 
# 1: Enabled. The node will use the suid scripts to mount and 
#    unmount the client shares using the SMB or CIFS file-
#    sharing protocol depending on which protocol is available
#    on both client and server side.
#
# 0: Disabled. The node will forbid any attempt to mount the
#    client shares.
#
EnableFileSharing = "1"

#
# Specify the path of the directory holding CUPS binaries (f.e. the
# 'lpoptions' program).
#
CUPSBinPath = "/usr/bin"

#
# Specify the path of the directory holding CUPS programs and reserved
# for administrative purposes (f.e. 'cupsd' or 'lpadmin').
#
CUPSSbinPath = "/usr/sbin"

#
# Enable or disable CUPS support:
#
# 1: Enabled. Enable CUPS support.
#
# 0: Disabled. Disable CUPS support.
#
EnableCUPSSupport = "1"

#
# Specify the file-sharing protocol to be used for attaching the
# filesystem to the target directory set by the ShareBasePath
# key. The possible values are both, smbfs, cifs or none. 
#
MountShareProtocol = "none"

#
# Specify the TCP port where the NX node SSHD daemon is running.
#
SSHDPort = "22"

#
# Accept or refuse the NX client connection if SSHD does not export
# the 'SSH_CONNECTION' and 'SSH_CLIENT' variables in the environment
# passed to the NX node.
#
# 1: Refuse. Check the remote IP and don't accept the connection if it
#    can't be determined.
#
# 0: Accept. Check the remote IP and accept the connection even if the
#    remote IP is not provided.
#
SSHDCheckIP = "0"

#
# Enable or disable running nxsensor:
#
# 1: Enabled.
#
# 0: Disabled.
# 
# Run the nxsensor daemon in the background. This daemon can be used
# to produce statistics about the node machine. Produced data is to
# be queried and elaborated by the nxstat daemon running on the NX
# server host machine.
#
EnableSensor = "0"

#
# Specify the hostname or IP address where the nxstat daemon, in
# charge of collecting and elaborating data provided by nxsensor,
# will be assumed to run.
#
StatisticsHost = "127.0.0.1"

#
# The port where the NX server will contact the nxsensor daemon to
# collect the statistics data. The key is also used by nxsensor to
# find out the network interface where it will listen for incoming
# connections.
#
NodeSensorPort = "19250"

#
# If set, the specified message will be provided to the user if this 
# is the first time the user starts a session on this node. 
#
NodeFirstLoginGreeting = "Welcome to your NX session"

#
# If set, the specified message will be provided to the user every
# time he/she has started a new session on this node.
#
NodeLoginGreeting = "Welcome to your NX session"

#
# Specify a different path from the default, i.e. user's home, where
# the .nx directory has to be created to store session files. If it
# doesn't exist yet, NX node will try to create a sub-directory for
# each of the users starting a session there, named as username, and
# will create the .nx under that sub-directory. For example, if this
# key is set to /tmp/nxdir/, when user nxtest runs the first session,
# the node will try to create the /tmp/nxdir/nxtest/.nx directory.
# The directory specifed in the UserNXDirectoryPath key needs to
# have proper ownership and permissions set to ensure that the node,
# running as the user, can access it. I.e. the directory should be
# writeable for all users or alternatively, the administrator should
# create a directory, with proper ownership and permissions, named as
# username, for each of the users who need to start sessions there.
#
UserNXDirectoryPath = ""

#
# Specify absolute path of the custom script to be executed before
# the session start-up. The script can accept session ID, username
# and session type as its input.
#
# E.g. UserScriptBeforeSessionStart = "/tmp/nxscript/script.sh"
#
UserScriptBeforeSessionStart = ""

#
# Specify absolute path of the custom script to be executed after the
# session start-up. The script can accept session ID, username and
# session type as its input.
#
UserScriptAfterSessionStart = ""

#
# Specify absolute path of the custom script to be executed before
# the session is suspended. The script can accept session ID and
# username as its input.
#
UserScriptBeforeSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed after the
# session is suspended. The script can accept session ID and username
# as its input.
#
UserScriptAfterSessionSuspend = ""

#
# Specify absolute path of the custom script to be executed before the
# session is closed. The script can accept session ID and username as
# its input.
#
UserScriptBeforeSessionClose = ""

#
# Specify absolute path of the custom script to be executed after the
# session is closed. The script can accept session ID and username as
# its input.
#
UserScriptAfterSessionClose = ""

#
# Specify absolute path of the custom script to be executed before
# the session is reconnected. The script can accept session ID and
# username as its input.
#
UserScriptBeforeSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after the
# session is reconnected. The script can accept session ID and user-
# name as its input.
#
UserScriptAfterSessionReconnect = ""

#
# Specify absolute path of the custom script to be executed after
# session failure. The script can accept session ID, username and
# session type as its input.
#
UserScriptAfterSessionFailure = ""

#
# Enable or disable the pulldown dialog, which provides a graphical
# way to suspend or terminate the rootless session:
#
# 1: Enabled. The pulldown menu is shown when the mouse pointer
#    moves near the middle of the top boundary of a window and
#    allows the user to suspend or terminate the session by means
#    of an icon-click.
#
# 0: Disabled. The ctrl+alt+T key combination has to be issued
#    to get the dialog for suspending or terminating the session.
#
EnablePulldownMenu = "1"

#
# Specify path and name of the command to start the GNOME session.
#
CommandStartGnome="/usr/bin/dbus-launch --exit-with-session gnome-session"

#
# Specify path and name of the command to start the KDE session.
#
CommandStartKDE="/usr/bin/dbus-launch --exit-with-session startkde"

#
# Specify path and name of the command to start the RDP Client.
#
CommandStartRDP="rdesktop -f"

#
# Specify path and name of the command to start the RFB Client.
#
CommandStartRFB="vncviewer -fullscreen"

```

And my /etc/ssh/sshd_config file look like this :

```

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin no
StrictModes yes 

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile      %h/.ssh/authorized_keys
#AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

```

When i check my NXserver status, i get this message :

```

NX> 900 Connecting to server ...
NX> 110 NX Server is running.
NX> 999 Bye.

```

However if i check a user :

```
/usr/NX/bin/nxserver --usercheck jpgauthier
NX> 900 Verifying public key authentication for NX user: jpgauthier.
NX> 900 Adding public key for user: jpgauthier to the authorized keys file.
NX> 716 Public key is already present in: /home/jpgauthier/.ssh/authorized_keys2.
NX> 900 Verifying public key authentication for NX user: jpgauthier.
NX> 500 ERROR: Public key authentication failed
NX> 500 WARNING: NX server was unable to login as user: jpgauthier
NX> 500 WARNING: Please check that the account is enabled to login.
NX> 500 WARNING: Also check that user's home directory, the directory
NX> 500 WARNING: ~/.ssh and the file ~/.ssh/authorized_keys2 have
NX> 500 WARNING: correct permissions according to the StrictModes of
NX> 500 WARNING: your SSHD configuration
NX> 999 Bye.
```

Any idea where is my problem?

Thanks :)

---

### Post by kevdog on 2007-12-11
Can you ssh into your box from a remote computer??  I would check this first since there seems to be a problem with public/private key authentication.

---

### Post by jpgauthier on 2007-12-11
yes im currently loged with SSH right now. The cat output i wrote in this post is from my remote box.... didnt had to type my password too, so i guess my keys are fine :S

---

### Post by kevdog on 2007-12-11
Again from what I remember about the older NX version, it generated a private key during the installation that you had to add to the NX user account.  Also verify settings in you sshd_config file.  My public keys were kept in the authorized_keys file, not authorized_keys2.  I had to make the change within the nx server config file.  

I wrote a guide about setting up FreeNx a while ago (in signature).  The information contained in this post is not up to date (so be forewarned).  However I would compare some of the installation steps in this guide to whatever documentation you are using.  I had a lot of problems installing the FreeNX server combination, so it gives some troubleshooting steps.  Take a peek at this guide to see if any of the information if applicable to you.  Just remember that some of the info may be dated!

---

### Post by jpgauthier on 2007-12-11
> **kevdog said:**
> Again from what I remember about the older NX version, it generated a private key during the installation that you had to add to the NX user account.  Also verify settings in you sshd_config file.  My public keys were kept in the authorized_keys file, not authorized_keys2.  I had to make the change within the nx server config file.  

I wrote a guide about setting up FreeNx a while ago (in signature).  The information contained in this post is not up to date (so be forewarned).  However I would compare some of the installation steps in this guide to whatever documentation you are using.  I had a lot of problems installing the FreeNX server combination, so it gives some troubleshooting steps.  Take a peek at this guide to see if any of the information if applicable to you.  Just remember that some of the info may be dated!

thanks Kevdog. I just uninstalled the whole nomachine stuff and followed your tutorial for freenx. Everything work perfectly now, server side. However, i guess the nx client from no machine on mac os X is not compatible or something because im getting a error **"The connection with the remote server was shut down. Please check the state of yoru network connection"** or maybe its just my firewall... If the port forwarding for ssh is open, everything should work right?

---

### Post by kevdog on 2007-12-11
Do a forum search -- my guide works, however it is dated.  The nomachine client should work with freenx.  The only problem I have had with freenx is with broken connections.  If the connection is suddenly broken without ending it appropriately, I can never log back in without having to delete the remnents of the old connections on both the server and client.  It kind of kills remote access until you do this.

Also the last freenx repository was for Feisty.  Not that this repository wont work, but I have not seen a seveas repository for gutsy.  Take a look at this thread also -- it is more updated if you are ever having a problem with freenx.

Good luck.  If you get everything up and running let me know

---

### Post by jpgauthier on 2007-12-11
```
-- NX SERVER START: -c /usr/lib/nx/nxserver - ORIG_COMMAND=
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: jpgauthier
NX> 102 Password: 
Info: Auth method: passdb 
NX> 103 Welcome to: golgoth user: jpgauthier
NX> 105 listsession --user="jpgauthier" --status="suspended,running" --geometry="1440x900x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'jpgauthier' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: jpgauthier
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --media="0" --session="Stargate" --type="unix-gnome" --geometry="1024x768+208+35" --kbtype="query" --screeninfo="1024x768x32+render" 

&link=adsl&backingstore=1&encryption=1&cache=16M&images=64M&media=0&session=Stargate&type=unix-gnome&geometry=1024x768+208+35&kbtype=query&screeninfo=1024x768x32+render&clientproto=1.5.0&user=jpgauthier&userip=0.0.0.0&uniqueid=490B96C2609FE15F63CE56CBF1AE9665&display=1001&host=127.0.0.1 
NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: golgoth-1001-490B96C2609FE15F63CE56CBF1AE9665
NX> 705 Session display: 1001
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: f0a80697700f28ea1bc4450d8f0f0a72
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: f0a80697700f28ea1bc4450d8f0f0a72
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 1006 Session status: running
NX> 105 bye
Bye
NX> 999 Bye
NX> 1004 Error: NX Agent exited with exit status 1.
NX> 1006 Session status: closed


```

I think my problem is right here :** NX> 1004 Error: NX Agent exited with exit status 1.**

Any idea what is error #1004 with status 1 ?!?

---

### Post by kevdog on 2007-12-11
Looks like you are having the same problem as me.  Be sure to clean out any old sessions that you had.  I can remember the folder where they are located both on client and server.  They are files that start something like:

C-8383939393304 and
S-839309543939

Basically C or S files with a long number after them.

I know its a pain.

---

### Post by jpgauthier on 2007-12-11
thanks again for the reply :)

Ok first of all, ive been using a new client since the lastest from nomachine is not gonna bring me anywhere. I found a MacOS X relase version 1.5. right after that, i had a lot more success. however, as you said, it look like im having a session issue. Found the C-name-01230123012031203 directory (its in ~/.nx by the way), delete it right away. Now im getting this...

```

NX> 203 NXSSH running with pid: 391
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: <hidden> on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.5.0-60 OS (GPL)
NX> 105 hello NXCLIENT - Version 1.5.0
NX> 134 Accepted protocol: 1.5.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: jpgauthier
NX> 102 Password: 
NX> 103 Welcome to: golgoth user: jpgauthier
NX> 105 listsession --user="jpgauthier" --status="suspended,running" --geometry="1440x900x32+render" --type="unix-gnome"
NX> 127 Sessions list of user 'jpgauthier' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: jpgauthier
NX> 105 startsession --session="mydomain" --type="unix-gnome" --cache="8M" --images="32M" --link="adsl" --nodelay="1" --encryption="1" --backingstore="when_requested" --geometry="1024x768+208+35" --media="0" --agent_server="" --agent_user="" agent_password="******""  --screeninfo="1024x768x32+render" 

NX> 1000 NXNODE - Version 1.5.0-60 OS (GPL)
NX> 700 Session id: golgoth-1000-D91DBC53BDC92574211411DB93E498FC
NX> 705 Session display: 1000
NX> 703 Session type: unix-gnome
NX> 701 Proxy cookie: 81af42074fbeadd45d7b237d52139713
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 81af42074fbeadd45d7b237d52139713
NX> 704 Session cache: unix-gnome
NX> 707 SSL tunneling: 1
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1.
/usr/lib/nx/nxserver: line 1190:  9487 Completed            sleep $AGENT_STARTUP_TIMEOUT
Can't open /var/lib/nxserver/db/running/sessionId{D91DBC53BDC92574211411DB93E498FC}:
`/var/lib/nxserver/db/running/sessionId{D91DBC53BDC92574211411DB93E498FC}': 
NX> 1006 Session status: closed
NX> 1001 Bye.
Killed by signal 15.

```

NX is searching for some non existing session ID folder. I went to /var/lib/nxserver/db/running/ and indeed, there is nothing in there. I'm almost there, not quite yet thought...

---

### Post by daflame on 2007-12-14
You could try to see if using the updated FreeNX 0.7.1 helps with the newer nx-3.0 libraries.  Here is a more recent edition:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

