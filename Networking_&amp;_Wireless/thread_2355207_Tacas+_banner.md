---
title: "Tacas+ banner"
date: 2017-03-10
forum: Networking &amp; Wireless
---

### Post by antokapo on 2017-03-10
Hi 

I'm trying to set up banner display at login from cisco router using tacacs+ server on Ubuntu 14.04 .

Every trila i've done was unsuccessful , at cisco router login i get always the default banner : 


"User Access Verification

Username:
"

in my conf. file i have : 

###################################################################
#   HOST AND SECRET
###################################################################


#host = *.*.*.* {
#type = cisco
#prompt = "TACACS+ Login"
#prompt = "Login ID: "
#}


host = *.*.*.* {
#       welcome banner = "\nTACACS+ Login\n"
#        prompt = "TACACS+ Login: "
}


( they're not working trials ... ) 

Have you any idea ? 


Thanks a lot 

Antonello

TACACS plus running as : 

tac_plus version F4.0.4.26
ACLS
FIONBIO
LIBWRAP
LINUX
LITTLE_ENDIAN
LOG_DAEMON
MAXSESS
MAXSESS_FINGER
PAM
NO_PWAGE
REAPCHILD
RETSIGTYPE RETSIGTYPE
SHADOW_PASSWORDS
SIGTSTP
SIGTTIN
SIGTTOU
SO_REUSEADDR
STRERROR
TAC_PLUS_PORT
UENABLE
__STDC__

---

