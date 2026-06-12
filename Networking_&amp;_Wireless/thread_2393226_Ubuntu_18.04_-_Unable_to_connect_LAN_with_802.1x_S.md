---
title: "Ubuntu 18.04 - Unable to connect LAN with 802.1x Security settings"
date: 2018-05-31
forum: Networking &amp; Wireless
---

### Post by fransvn2 on 2018-05-31
I am experiencing issues connecting to a corporate LAN using 802.1x. The logs indicate the authentication was successful, but then fails with

"Activation: (ethernet) association took too long."

It seems to be happening with WIFI connection as well. I have found posts indicating I should execute 'killall wpa_supplicant', which I tried but it did not work

May 31 09:59:30 machine1 NetworkManager[1295]: <info>  [1527753570.0225] settings-connection[0x564867ba3440,e4340a74-d34c-3c4d-9a85-3898c271563f]: write: successfully updated (keyfile: update /etc/NetworkManager/system-connections/Wired connection 1 (e4340a74-d34c-3c4d-9a85-3898c271563f,"Wired connection 1"))
May 31 09:59:30 machine1 NetworkManager[1295]: <info>  [1527753570.0233] audit: op="connection-update" uuid="e4340a74-d34c-3c4d-9a85-3898c271563f" name="Wired connection 1" args="802-1x.identity" pid=3275 uid=1000 result="success"
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8458] device (enp0s31f6): Activation: starting connection 'Wired connection 1' (e4340a74-d34c-3c4d-9a85-3898c271563f)
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8462] audit: op="connection-activate" uuid="e4340a74-d34c-3c4d-9a85-3898c271563f" name="Wired connection 1" pid=3275 uid=1000 result="success"
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8469] device (enp0s31f6): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8482] device (enp0s31f6): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8492] device (enp0s31f6): Activation: (ethernet) connection 'Wired connection 1' has security, but secrets are required.
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8497] device (enp0s31f6): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 gnome-shell[2412]: clutter_input_focus_set_cursor_location: assertion 'clutter_input_focus_is_focused (focus)' failed
May 31 09:59:49 machine1 gnome-shell[2412]: clutter_input_focus_set_cursor_location: assertion 'clutter_input_focus_is_focused (focus)' failed
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8209] settings-connection[0x564867ba3440,e4340a74-d34c-3c4d-9a85-3898c271563f]: write: successfully updated (keyfile: update /etc/NetworkManager/system-connections/Wired connection 1 (e4340a74-d34c-3c4d-9a85-3898c271563f,"Wired connection 1")), connection was modified in the process
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8308] device (enp0s31f6): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8312] device (enp0s31f6): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8318] device (enp0s31f6): Activation: (ethernet) connection 'Wired connection 1' requires no security. No secrets needed.
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: Failed to construct signal
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9040] device (enp0s31f6): supplicant interface state: starting -> ready
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'password' value '<hidden>'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'key_mgmt' value 'IEEE8021X'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'eapol_flags' value '0'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'eap' value 'PEAP'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'fragment_size' value '1266'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'phase2' value 'auth=MSCHAPV2'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'ca_cert' value '/home/user1/certificates/certificate.pem'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9042] Config: added 'identity' value 'companyjnb01\f4679148'
May 31 09:59:53 machine1 wpa_supplicant[1296]: enp0s31f6: Associated with 01:80:c2:00:00:03
May 31 09:59:53 machine1 wpa_supplicant[1296]: WMM AC: Missing IEs
May 31 09:59:53 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9107] device (enp0s31f6): supplicant interface state: ready -> associated
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-STARTED EAP authentication started
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=13 -> NAK
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=3 subject='XXX' hash=431e5a6df18b7130013bb8c0a5740f1e496e9912079db3574c0aa0b3e7c616dc
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='XXX 1' hash=2ae39ca8d3c0d3f66674cd73ff4debf1d2401003a342c885b1f7
78d9e38d8fd7
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='XXX 2' hash=91222b0799303f999215df8f22825cda3c073df5b63ce47d
832015d6a151231d
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='XXX 3' hash=53647
817376a0052b4aa01ada379d8ccfff0a9aee71ffd7d2a69bf8e7b61af0c
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-ALT depth=0 DNS:dns.company.co.za
May 31 09:59:56 machine1 wpa_supplicant[1296]: EAP-MSCHAPV2: Authentication succeeded
May 31 09:59:56 machine1 wpa_supplicant[1296]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
May 31 10:00:19 machine1 NetworkManager[1295]: <warn>  [1527753619.2436] device (enp0s31f6): Activation: (ethernet) association took too long.
May 31 10:00:19 machine1 NetworkManager[1295]: <info>  [1527753619.2441] device (enp0s31f6): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May 31 10:00:19 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-DISCONNECTED bssid=01:80:c2:00:00:03 reason=3 locally_generated=1

I am running Ubuntu 18.04 LTS

---

### Post by mIk3_08 on 2018-05-31
> **fransvn2 said:**
> I am experiencing issues connecting to a corporate LAN using 802.1x. The logs indicate the authentication was successful, but then fails with

"Activation: (ethernet) association took too long."

It seems to be happening with WIFI connection as well. I have found posts indicating I should execute 'killall wpa_supplicant', which I tried but it did not work

May 31 09:59:30 machine1 NetworkManager[1295]: <info>  [1527753570.0225] settings-connection[0x564867ba3440,e4340a74-d34c-3c4d-9a85-3898c271563f]: write: successfully updated (keyfile: update /etc/NetworkManager/system-connections/Wired connection 1 (e4340a74-d34c-3c4d-9a85-3898c271563f,"Wired connection 1"))
May 31 09:59:30 machine1 NetworkManager[1295]: <info>  [1527753570.0233] audit: op="connection-update" uuid="e4340a74-d34c-3c4d-9a85-3898c271563f" name="Wired connection 1" args="802-1x.identity" pid=3275 uid=1000 result="success"
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8458] device (enp0s31f6): Activation: starting connection 'Wired connection 1' (e4340a74-d34c-3c4d-9a85-3898c271563f)
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8462] audit: op="connection-activate" uuid="e4340a74-d34c-3c4d-9a85-3898c271563f" name="Wired connection 1" pid=3275 uid=1000 result="success"
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8469] device (enp0s31f6): state change: disconnected -> prepare (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8482] device (enp0s31f6): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8492] device (enp0s31f6): Activation: (ethernet) connection 'Wired connection 1' has security, but secrets are required.
May 31 09:59:49 machine1 NetworkManager[1295]: <info>  [1527753589.8497] device (enp0s31f6): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May 31 09:59:49 machine1 gnome-shell[2412]: clutter_input_focus_set_cursor_location: assertion 'clutter_input_focus_is_focused (focus)' failed
May 31 09:59:49 machine1 gnome-shell[2412]: clutter_input_focus_set_cursor_location: assertion 'clutter_input_focus_is_focused (focus)' failed
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8209] settings-connection[0x564867ba3440,e4340a74-d34c-3c4d-9a85-3898c271563f]: write: successfully updated (keyfile: update /etc/NetworkManager/system-connections/Wired connection 1 (e4340a74-d34c-3c4d-9a85-3898c271563f,"Wired connection 1")), connection was modified in the process
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8308] device (enp0s31f6): state change: need-auth -> prepare (reason 'none', sys-iface-state: 'managed')
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8312] device (enp0s31f6): state change: prepare -> config (reason 'none', sys-iface-state: 'managed')
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.8318] device (enp0s31f6): Activation: (ethernet) connection 'Wired connection 1' requires no security. No secrets needed.
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: Failed to construct signal
May 31 09:59:53 machine1 wpa_supplicant[1296]: dbus: fill_dict_with_properties dbus_interface=fi.w1.wpa_supplicant1.Interface dbus_property=Stations getter failed
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9040] device (enp0s31f6): supplicant interface state: starting -> ready
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'password' value '<hidden>'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'key_mgmt' value 'IEEE8021X'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'eapol_flags' value '0'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'eap' value 'PEAP'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'fragment_size' value '1266'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'phase2' value 'auth=MSCHAPV2'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9041] Config: added 'ca_cert' value '/home/user1/certificates/certificate.pem'
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9042] Config: added 'identity' value 'companyjnb01\f4679148'
May 31 09:59:53 machine1 wpa_supplicant[1296]: enp0s31f6: Associated with 01:80:c2:00:00:03
May 31 09:59:53 machine1 wpa_supplicant[1296]: WMM AC: Missing IEs
May 31 09:59:53 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
May 31 09:59:53 machine1 NetworkManager[1295]: <info>  [1527753593.9107] device (enp0s31f6): supplicant interface state: ready -> associated
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-STARTED EAP authentication started
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=13 -> NAK
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
May 31 09:59:55 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=3 subject='XXX' hash=431e5a6df18b7130013bb8c0a5740f1e496e9912079db3574c0aa0b3e7c616dc
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=2 subject='XXX 1' hash=2ae39ca8d3c0d3f66674cd73ff4debf1d2401003a342c885b1f7
78d9e38d8fd7
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=1 subject='XXX 2' hash=91222b0799303f999215df8f22825cda3c073df5b63ce47d
832015d6a151231d
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='XXX 3' hash=53647
817376a0052b4aa01ada379d8ccfff0a9aee71ffd7d2a69bf8e7b61af0c
May 31 09:59:56 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-EAP-PEER-ALT depth=0 DNS:dns.company.co.za
May 31 09:59:56 machine1 wpa_supplicant[1296]: EAP-MSCHAPV2: Authentication succeeded
May 31 09:59:56 machine1 wpa_supplicant[1296]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
May 31 10:00:19 machine1 NetworkManager[1295]: <warn>  [1527753619.2436] device (enp0s31f6): Activation: (ethernet) association took too long.
May 31 10:00:19 machine1 NetworkManager[1295]: <info>  [1527753619.2441] device (enp0s31f6): state change: config -> need-auth (reason 'none', sys-iface-state: 'managed')
May 31 10:00:19 machine1 wpa_supplicant[1296]: enp0s31f6: CTRL-EVENT-DISCONNECTED bssid=01:80:c2:00:00:03 reason=3 locally_generated=1

I am running Ubuntu 18.04 LTS


Try to run Bleachbit Admin and clean your machine. Then try to restart after.

---

