---
title: "SIM registration Issue"
date: 2024-02-15
forum: Networking &amp; Wireless
---

### Post by gharshr-gd on 2024-02-15
I am using Dell Edge Gateway 3000 series. 

It has a modem attached with it. After inserting the SIM, the modem manager creates the modem successfully. But, it continuously goes into searching state. 

After certain retries it sends a indication as below

#
ModemManager[18371]: [/dev/cdc-wdm1] received generic indication (translated)...
<<<<<< QMUX:
<<<<<<   length  = 68
<<<<<<   flags   = 0x80
<<<<<<   service = "nas"
<<<<<<   client  = 3
<<<<<< QMI:
<<<<<<   flags       = "indication"
<<<<<<   transaction = 134
<<<<<<   tlv_length  = 56
<<<<<<   message     = "Serving System" (0x0024)
<<<<<< TLV:
<<<<<<   type       = "Serving System" (0x01)
<<<<<<   length     = 6
<<<<<<   value      = 03:02:02:02:01:05
<<<<<<   translated = [ registration_state = 'registration-denied' cs_attach_state = 'detached' ps_attach_state = 'detached' selected_network = '3gpp' radio_interfaces = '{ [0] = 'umts '}' ]<<<<<< TLV:
<<<<<<   type       = "Roaming Indicator" (0x10)
<<<<<<   length     = 1
<<<<<<   value      = 00
<<<<<<   translated = on
<<<<<< TLV:
<<<<<<   type       = "Data Service Capability" (0x11)
<<<<<<   length     = 1
<<<<<<   value      = 00
<<<<<<   translated = {}
<<<<<< TLV:
<<<<<<   type       = "Current PLMN" (0x12)
<<<<<<   length     = 5
<<<<<<   value      = F4:00:5B:00:00
<<<<<<   translated = [ mcc = '244' mnc = '91' description = '' ]
<<<<<< TLV:
<<<<<<   type       = "Roaming Indicator List" (0x15)
<<<<<<   length     = 3
<<<<<<   value      = 01:05:00
<<<<<<   translated = { [0] = '[ radio_interface = 'umts' roaming_indicator = 'on' ] '}
<<<<<< TLV:
<<<<<<   type       = "Detailed Service Status" (0x22)
<<<<<<   length     = 5
<<<<<<   value      = 01:03:00:00:01
<<<<<<   translated = [ status = 'limited' capability = 'cs-ps' hdr_status = 'none' hdr_hybrid = 'no' forbidden = 'yes' ]
<<<<<< TLV:
<<<<<<   type       = "UMTS Primary Scrambling Code" (0x28)
<<<<<<   length     = 2
<<<<<<   value      = 75:01
<<<<<<   translated = 373
<<<<<< TLV:
<<<<<<   type       = "MNC PCS Digit Include Status" (0x29)
<<<<<<   length     = 5
<<<<<<   value      = F4:00:5B:00:00
<<<<<<   translated = [ mcc = '244' mnc = '91' includes_pcs_digit = 'no' ]
<<<<<< TLV:
<<<<<<   type   = 0x2a
<<<<<<   length = 1
<<<<<<   value  = 00                                                                                                                                                     
#

Then it continues searching again, and this process goes on and on

What can be the reason for registration denied, as even after discussing with the service provider, they say, immediately after establishing a session, the DELL machine requests session termination

---

