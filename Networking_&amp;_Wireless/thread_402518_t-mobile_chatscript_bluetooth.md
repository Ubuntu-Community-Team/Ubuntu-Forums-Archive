---
title: "t-mobile chatscript bluetooth"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by mimsmall on 2007-04-05
I'm attempting to use my Nokia 3660 as a modem. T-mobile told me that my phone was compatible. I signed on for the add-on data package. 

This is my connect script:

TIMEOUT 10
ABORT   'BUSY'
ABORT   'NO ANSWER'
ABORT   'ERROR'
SAY     'Starting GPRS connect script\n'

# Get the modem's attention and reset it.
""      'ATZ'

# E0=No echo, V1=English result codes
OK      'ATE0V1'

# Set Access Point Name (APN)
SAY     'Setting APN\n'
OK      'AT+CGDCONT=1,"IP","internet3.voicestream.com"'

# Dial the number
ABORT   'NO CARRIER'
SAY     'Dialing...\n'
OK      'ATD*99***1#'
CONNECT ''

This the output of plog:

@donald:~$ plog
Apr  5 21:21:12 localhost pppd[21597]: rcvd [IPCP ConfReq id=0x0 <addr 10.6.6.6>]
Apr  5 21:21:12 localhost pppd[21597]: sent [IPCP ConfAck id=0x0 <addr 10.6.6.6>]
Apr  5 21:21:12 localhost pppd[21597]: rcvd [LCP ProtRej id=0x0 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Apr  5 21:21:12 localhost pppd[21597]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Apr  5 21:21:13 localhost pppd[21597]: rcvd [LCP TermReq id=0x1]
Apr  5 21:21:13 localhost pppd[21597]: LCP terminated by peer
Apr  5 21:21:13 localhost pppd[21597]: sent [LCP TermAck id=0x1]
Apr  5 21:21:16 localhost pppd[21597]: Connection terminated.
Apr  5 21:21:17 localhost pppd[21597]: Modem hangup
Apr  5 21:21:17 localhost pppd[21597]: Exit.

What do I need to change. The connect script is the last one I tried, other people's scripts give similar results.

---

