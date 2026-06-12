---
title: "compiling wpa_supplicant with wlioctl.h for broadcom wireless card"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by ample on 2008-08-01
can someone post how to compile wpa_supplicant with wlioctl.h to use the broadcom driver?  i tried simply copying wlioctl.h into the wpa_supplicant extracted folder and typing "make" but i got about 100 errors.  im pretty sure it has to do with the .config file i automatically generated since the errors were in config.c.  

errors:
```
config.c: In function ‘wpa_config_write_str’:
config.c:193: error: ‘size_t’ undeclared (first use in this function)
config.c:193: error: expected ‘;’ before ‘len’
config.c:196: error: ‘u8’ undeclared (first use in this function)
config.c:196: error: expected expression before ‘)’ token
config.c:197: error: ‘NULL’ undeclared (first use in this function)
config.c:201: error: ‘len’ undeclared (first use in this function)
config.c:201: error: expected expression before ‘)’ token
config.c:201: error: expected ‘)’ before ‘ssid’
config.c:203: warning: incompatible implicit declaration of built-in function ‘strlen’
config.c:205: warning: implicit declaration of function ‘wpa_config_write_string’
config.c:205: error: expected ‘)’ before ‘u8’
config.c:205: warning: type defaults to ‘int’ in declaration of ‘type name’
config.c:205: warning: return makes pointer from integer without a cast
config.c: In function ‘wpa_config_parse_int’:
config.c:215: error: ‘u8’ undeclared (first use in this function)
config.c:215: error: expected expression before ‘)’ token
config.c:216: warning: implicit declaration of function ‘atoi’
config.c: In function ‘wpa_config_write_int’:
config.c:245: error: ‘u8’ undeclared (first use in this function)
config.c:245: error: expected expression before ‘)’ token
config.c:247: warning: incompatible implicit declaration of built-in function ‘malloc’
config.c:248: error: ‘NULL’ undeclared (first use in this function)
config.c:250: warning: implicit declaration of function ‘snprintf’
config.c:250: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: In function ‘wpa_config_parse_bssid’:
config.c:260: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:260: error: too many arguments to function ‘hwaddr_aton’
config.c:265: error: ‘struct wpa_ssid’ has no member named ‘bssid_set’
config.c:266: warning: implicit declaration of function ‘wpa_hexdump’
config.c:266: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c: In function ‘wpa_config_write_bssid’:
config.c:276: error: ‘struct wpa_ssid’ has no member named ‘bssid_set’
config.c:277: error: ‘NULL’ undeclared (first use in this function)
config.c:279: warning: incompatible implicit declaration of built-in function ‘malloc’
config.c:282: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c:282: error: ‘struct wpa_ssid’ has no member named ‘bssid’
config.c: In function ‘wpa_config_parse_psk’:
config.c:294: error: ‘size_t’ undeclared (first use in this function)
config.c:294: error: expected ‘;’ before ‘len’
config.c:297: warning: incompatible implicit declaration of built-in function ‘strrchr’
config.c:299: error: ‘len’ undeclared (first use in this function)
config.c:301: warning: incompatible implicit declaration of built-in function ‘strlen’
config.c:309: error: ‘u8’ undeclared (first use in this function)
config.c:309: error: expected expression before ‘)’ token
config.c:310: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:310: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:311: warning: implicit declaration of function ‘memcmp’
config.c:311: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:313: error: ‘struct wpa_ssid’ has no member named ‘psk_set’
config.c:314: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:315: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:315: warning: incompatible implicit declaration of built-in function ‘malloc’
config.c:316: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:316: error: ‘NULL’ undeclared (first use in this function)
config.c:318: warning: implicit declaration of function ‘memcpy’
config.c:318: warning: incompatible implicit declaration of built-in function ‘memcpy’
config.c:318: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:319: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:323: error: ‘struct wpa_ssid’ has no member named ‘psk’
config.c:323: error: too many arguments to function ‘hexstr2bin’
config.c:330: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:331: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:333: error: ‘struct wpa_ssid’ has no member named ‘psk_set’
config.c:334: warning: implicit declaration of function ‘wpa_hexdump_key’
config.c:334: error: ‘struct wpa_ssid’ has no member named ‘psk’
config.c: In function ‘wpa_config_write_psk’:
config.c:342: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:343: warning: implicit declaration of function ‘wpa_config_write_string_ascii’
config.c:344: error: expected ‘)’ before ‘u8’
config.c:344: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:344: warning: type defaults to ‘int’ in declaration of ‘type name’
config.c:345: warning: incompatible implicit declaration of built-in function ‘strlen’
config.c:345: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:345: warning: return makes pointer from integer without a cast
config.c:347: error: ‘struct wpa_ssid’ has no member named ‘psk_set’
config.c:348: warning: implicit declaration of function ‘wpa_config_write_string_hex’
config.c:348: error: ‘struct wpa_ssid’ has no member named ‘psk’
config.c:348: warning: return makes pointer from integer without a cast
config.c:350: error: ‘NULL’ undeclared (first use in this function)
config.c: In function ‘wpa_config_parse_proto’:
config.c:361: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:362: error: ‘NULL’ undeclared (first use in this function)
config.c:376: warning: implicit declaration of function ‘strcmp’
config.c:400: error: ‘struct wpa_ssid’ has no member named ‘proto’
config.c: In function ‘wpa_config_write_proto’:
config.c:411: warning: implicit declaration of function ‘os_zalloc’
config.c:411: warning: assignment makes pointer from integer without a cast
config.c:412: error: ‘NULL’ undeclared (first use in this function)
config.c:416: error: ‘struct wpa_ssid’ has no member named ‘proto’
config.c:417: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:424: error: ‘struct wpa_ssid’ has no member named ‘proto’
config.c:425: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: In function ‘wpa_config_parse_key_mgmt’:
config.c:443: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:444: error: ‘NULL’ undeclared (first use in this function)
config.c:487: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c: In function ‘wpa_config_write_key_mgmt’:
config.c:498: warning: assignment makes pointer from integer without a cast
config.c:499: error: ‘NULL’ undeclared (first use in this function)
config.c:503: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:504: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:513: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:514: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:523: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:524: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:533: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:534: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:543: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:544: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: In function ‘wpa_config_parse_cipher’:
config.c:562: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:563: error: ‘NULL’ undeclared (first use in this function)
config.c: In function ‘wpa_config_write_cipher’:
config.c:614: warning: assignment makes pointer from integer without a cast
config.c:615: error: ‘NULL’ undeclared (first use in this function)
config.c:620: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:630: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:640: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:650: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:660: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: In function ‘wpa_config_parse_pairwise’:
config.c:688: error: ‘struct wpa_ssid’ has no member named ‘pairwise_cipher’
config.c: In function ‘wpa_config_write_pairwise’:
config.c:696: error: ‘struct wpa_ssid’ has no member named ‘pairwise_cipher’
config.c: In function ‘wpa_config_parse_group’:
config.c:716: error: ‘struct wpa_ssid’ has no member named ‘group_cipher’
config.c: In function ‘wpa_config_write_group’:
config.c:724: error: ‘struct wpa_ssid’ has no member named ‘group_cipher’
config.c: In function ‘wpa_config_parse_auth_alg’:
config.c:735: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:736: error: ‘NULL’ undeclared (first use in this function)
config.c:775: error: ‘struct wpa_ssid’ has no member named ‘auth_alg’
config.c: In function ‘wpa_config_write_auth_alg’:
config.c:786: warning: assignment makes pointer from integer without a cast
config.c:787: error: ‘NULL’ undeclared (first use in this function)
config.c:791: error: ‘struct wpa_ssid’ has no member named ‘auth_alg’
config.c:792: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:801: error: ‘struct wpa_ssid’ has no member named ‘auth_alg’
config.c:802: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c:811: error: ‘struct wpa_ssid’ has no member named ‘auth_alg’
config.c:812: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: In function ‘wpa_config_parse_eap’:
config.c:832: error: ‘NULL’ undeclared (first use in this function)
config.c:833: error: ‘size_t’ undeclared (first use in this function)
config.c:833: error: expected ‘;’ before ‘num_methods’
config.c:835: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:851: warning: implicit declaration of function ‘realloc’
config.c:851: error: ‘num_methods’ undeclared (first use in this function)
config.c:851: warning: assignment makes pointer from integer without a cast
config.c:871: error: ‘struct wpa_ssid’ has no member named ‘leap’
config.c:873: error: ‘struct wpa_ssid’ has no member named ‘non_leap’
config.c:882: warning: assignment makes pointer from integer without a cast
config.c:892: error: ‘u8’ undeclared (first use in this function)
config.c:892: error: expected expression before ‘)’ token
config.c:893: error: ‘struct wpa_ssid’ has no member named ‘eap_methods’
config.c: In function ‘wpa_config_write_eap’:
config.c:903: error: ‘struct wpa_ssid’ has no member named ‘eap_methods’
config.c:906: error: ‘NULL’ undeclared (first use in this function)
config.c:909: warning: assignment makes pointer from integer without a cast
config.c:915: error: ‘const struct eap_method_type’ has no member named ‘method’
config.c:917: error: ‘const struct eap_method_type’ has no member named ‘method’
config.c:919: warning: incompatible implicit declaration of built-in function ‘snprintf’
config.c: At top level:
config.c:934: error: expected ‘)’ before ‘*’ token
config.c: In function ‘wpa_config_parse_wep_key0’:
config.c:963: warning: implicit declaration of function ‘wpa_config_parse_wep_key’
config.c:963: error: ‘struct wpa_ssid’ has no member named ‘wep_key’
config.c:964: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c: In function ‘wpa_config_parse_wep_key1’:
config.c:973: error: ‘struct wpa_ssid’ has no member named ‘wep_key’
config.c:974: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c: In function ‘wpa_config_parse_wep_key2’:
config.c:983: error: ‘struct wpa_ssid’ has no member named ‘wep_key’
config.c:984: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c: In function ‘wpa_config_parse_wep_key3’:
config.c:993: error: ‘struct wpa_ssid’ has no member named ‘wep_key’
config.c:994: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c: In function ‘wpa_config_write_wep_key’:
config.c:1001: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c:1002: error: ‘NULL’ undeclared (first use in this function)
config.c:1003: error: ‘struct wpa_ssid’ has no member named ‘wep_key’
config.c:1004: error: ‘struct wpa_ssid’ has no member named ‘wep_key_len’
config.c:1004: warning: return makes pointer from integer without a cast
config.c: At top level:
config.c:1102: error: ‘struct wpa_ssid’ has no member named ‘ssid’
config.c:1102: error: ‘struct wpa_ssid’ has no member named ‘ssid_len’
config.c:1103: error: ‘struct wpa_ssid’ has no member named ‘scan_ssid’
config.c:1104: error: ‘NULL’ undeclared here (not in a function)
config.c:1113: error: ‘struct wpa_ssid’ has no member named ‘identity’
config.c:1113: error: ‘struct wpa_ssid’ has no member named ‘identity_len’
config.c:1114: error: ‘struct wpa_ssid’ has no member named ‘anonymous_identity’
config.c:1114: error: ‘struct wpa_ssid’ has no member named ‘anonymous_identity_len’
config.c:1115: error: ‘struct wpa_ssid’ has no member named ‘eappsk’
config.c:1115: error: ‘struct wpa_ssid’ has no member named ‘eappsk_len’
config.c:1116: error: ‘struct wpa_ssid’ has no member named ‘nai’
config.c:1116: error: ‘struct wpa_ssid’ has no member named ‘nai_len’
config.c:1117: error: ‘struct wpa_ssid’ has no member named ‘password’
config.c:1117: error: ‘struct wpa_ssid’ has no member named ‘password_len’
config.c:1118: error: ‘struct wpa_ssid’ has no member named ‘ca_cert’
config.c:1119: error: ‘struct wpa_ssid’ has no member named ‘ca_path’
config.c:1120: error: ‘struct wpa_ssid’ has no member named ‘client_cert’
config.c:1121: error: ‘struct wpa_ssid’ has no member named ‘private_key’
config.c:1122: error: ‘struct wpa_ssid’ has no member named ‘private_key_passwd’
config.c:1123: error: ‘struct wpa_ssid’ has no member named ‘dh_file’
config.c:1124: error: ‘struct wpa_ssid’ has no member named ‘subject_match’
config.c:1125: error: ‘struct wpa_ssid’ has no member named ‘altsubject_match’
config.c:1126: error: ‘struct wpa_ssid’ has no member named ‘ca_cert2’
config.c:1127: error: ‘struct wpa_ssid’ has no member named ‘ca_path2’
config.c:1128: error: ‘struct wpa_ssid’ has no member named ‘client_cert2’
config.c:1129: error: ‘struct wpa_ssid’ has no member named ‘private_key2’
config.c:1130: error: ‘struct wpa_ssid’ has no member named ‘private_key2_passwd’
config.c:1131: error: ‘struct wpa_ssid’ has no member named ‘dh_file2’
config.c:1132: error: ‘struct wpa_ssid’ has no member named ‘subject_match2’
config.c:1133: error: ‘struct wpa_ssid’ has no member named ‘altsubject_match2’
config.c:1134: error: ‘struct wpa_ssid’ has no member named ‘phase1’
config.c:1135: error: ‘struct wpa_ssid’ has no member named ‘phase2’
config.c:1136: error: ‘struct wpa_ssid’ has no member named ‘pcsc’
config.c:1137: error: ‘struct wpa_ssid’ has no member named ‘pin’
config.c:1138: error: ‘struct wpa_ssid’ has no member named ‘engine_id’
config.c:1139: error: ‘struct wpa_ssid’ has no member named ‘key_id’
config.c:1140: error: ‘struct wpa_ssid’ has no member named ‘engine’
config.c:1141: error: ‘struct wpa_ssid’ has no member named ‘eapol_flags’
config.c:1147: error: ‘struct wpa_ssid’ has no member named ‘wep_tx_keyidx’
config.c:1150: error: ‘struct wpa_ssid’ has no member named ‘eap_workaround’
config.c:1151: error: ‘struct wpa_ssid’ has no member named ‘pac_file’
config.c:1152: error: ‘struct wpa_ssid’ has no member named ‘fragment_size’
config.c:1154: error: ‘struct wpa_ssid’ has no member named ‘mode’
config.c:1155: error: ‘struct wpa_ssid’ has no member named ‘proactive_key_caching’
config.c:1156: error: ‘struct wpa_ssid’ has no member named ‘disabled’
config.c:1157: error: ‘struct wpa_ssid’ has no member named ‘id_str’
config.c:1161: error: ‘struct wpa_ssid’ has no member named ‘peerkey’
config.c:1162: error: ‘struct wpa_ssid’ has no member named ‘mixed_cell’
config.c:1163: error: ‘struct wpa_ssid’ has no member named ‘frequency’
config.c: In function ‘wpa_config_add_prio_network’:
config.c:1217: warning: assignment makes pointer from integer without a cast
config.c:1219: warning: comparison of distinct pointer types lacks a cast
config.c:1227: warning: implicit declaration of function ‘memmove’
config.c:1227: warning: incompatible implicit declaration of built-in function ‘memmove’
config.c: In function ‘wpa_config_update_prio_list’:
config.c:1253: warning: assignment from incompatible pointer type
config.c:1258: warning: assignment from incompatible pointer type
config.c: In function ‘wpa_config_free_ssid’:
config.c:1277: error: ‘struct wpa_ssid’ has no member named ‘ssid’
config.c:1278: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:1280: error: ‘struct wpa_ssid’ has no member named ‘eap_methods’
config.c:1281: error: ‘struct wpa_ssid’ has no member named ‘identity’
config.c:1282: error: ‘struct wpa_ssid’ has no member named ‘anonymous_identity’
config.c:1283: error: ‘struct wpa_ssid’ has no member named ‘eappsk’
config.c:1284: error: ‘struct wpa_ssid’ has no member named ‘nai’
config.c:1285: error: ‘struct wpa_ssid’ has no member named ‘password’
config.c:1286: error: ‘struct wpa_ssid’ has no member named ‘ca_cert’
config.c:1287: error: ‘struct wpa_ssid’ has no member named ‘ca_path’
config.c:1288: error: ‘struct wpa_ssid’ has no member named ‘client_cert’
config.c:1289: error: ‘struct wpa_ssid’ has no member named ‘private_key’
config.c:1290: error: ‘struct wpa_ssid’ has no member named ‘private_key_passwd’
config.c:1291: error: ‘struct wpa_ssid’ has no member named ‘dh_file’
config.c:1292: error: ‘struct wpa_ssid’ has no member named ‘subject_match’
config.c:1293: error: ‘struct wpa_ssid’ has no member named ‘altsubject_match’
config.c:1294: error: ‘struct wpa_ssid’ has no member named ‘ca_cert2’
config.c:1295: error: ‘struct wpa_ssid’ has no member named ‘ca_path2’
config.c:1296: error: ‘struct wpa_ssid’ has no member named ‘client_cert2’
config.c:1297: error: ‘struct wpa_ssid’ has no member named ‘private_key2’
config.c:1298: error: ‘struct wpa_ssid’ has no member named ‘private_key2_passwd’
config.c:1299: error: ‘struct wpa_ssid’ has no member named ‘dh_file2’
config.c:1300: error: ‘struct wpa_ssid’ has no member named ‘subject_match2’
config.c:1301: error: ‘struct wpa_ssid’ has no member named ‘altsubject_match2’
config.c:1302: error: ‘struct wpa_ssid’ has no member named ‘phase1’
config.c:1303: error: ‘struct wpa_ssid’ has no member named ‘phase2’
config.c:1304: error: ‘struct wpa_ssid’ has no member named ‘pcsc’
config.c:1305: error: ‘struct wpa_ssid’ has no member named ‘pin’
config.c:1306: error: ‘struct wpa_ssid’ has no member named ‘engine_id’
config.c:1307: error: ‘struct wpa_ssid’ has no member named ‘key_id’
config.c:1308: error: ‘struct wpa_ssid’ has no member named ‘otp’
config.c:1309: error: ‘struct wpa_ssid’ has no member named ‘pending_req_otp’
config.c:1310: error: ‘struct wpa_ssid’ has no member named ‘pac_file’
config.c:1311: error: ‘struct wpa_ssid’ has no member named ‘new_password’
config.c:1313: error: ‘struct wpa_ssid’ has no member named ‘id_str’
config.c: In function ‘wpa_config_free’:
config.c:1328: warning: initialization from incompatible pointer type
config.c:1337: warning: assignment from incompatible pointer type
config.c:1340: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1340: warning: assignment from incompatible pointer type
config.c: At top level:
config.c:1364: error: expected declaration specifiers or ‘...’ before ‘u32’
config.c: In function ‘wpa_config_allowed_eap_method’:
config.c:1369: warning: comparison of distinct pointer types lacks a cast
config.c:1369: error: ‘struct wpa_ssid’ has no member named ‘eap_methods’
config.c:1372: error: ‘struct wpa_ssid’ has no member named ‘eap_methods’
config.c:1372: warning: assignment from incompatible pointer type
config.c:1374: error: ‘struct eap_method_type’ has no member named ‘method’
config.c:1375: error: ‘struct eap_method_type’ has no member named ‘method’
config.c:1375: error: ‘method’ undeclared (first use in this function)
config.c: In function ‘wpa_config_add_network’:
config.c:1412: warning: initialization from incompatible pointer type
config.c:1424: warning: assignment makes pointer from integer without a cast
config.c:1425: warning: comparison of distinct pointer types lacks a cast
config.c:1426: warning: return from incompatible pointer type
config.c: In function ‘wpa_config_remove_network’:
config.c:1447: warning: initialization from incompatible pointer type
config.c:1457: warning: comparison of distinct pointer types lacks a cast
config.c: In function ‘wpa_config_set_network_defaults’:
config.c:1477: error: ‘struct wpa_ssid’ has no member named ‘proto’
config.c:1477: warning: statement with no effect
config.c:1478: error: ‘struct wpa_ssid’ has no member named ‘pairwise_cipher’
config.c:1478: warning: statement with no effect
config.c:1479: error: ‘struct wpa_ssid’ has no member named ‘group_cipher’
config.c:1479: warning: statement with no effect
config.c:1480: error: ‘struct wpa_ssid’ has no member named ‘key_mgmt’
config.c:1480: warning: statement with no effect
config.c:1482: error: ‘struct wpa_ssid’ has no member named ‘eapol_flags’
config.c:1482: warning: statement with no effect
config.c:1483: error: ‘struct wpa_ssid’ has no member named ‘eap_workaround’
config.c:1483: warning: statement with no effect
config.c:1484: error: ‘struct wpa_ssid’ has no member named ‘fragment_size’
config.c:1484: warning: statement with no effect
config.c: In function ‘wpa_config_set’:
config.c:1505: error: ‘size_t’ undeclared (first use in this function)
config.c:1505: warning: statement with no effect
config.c:1505: error: expected ‘;’ before ‘i’
config.c:1508: warning: comparison of distinct pointer types lacks a cast
config.c:1508: warning: comparison of distinct pointer types lacks a cast
config.c:1508: warning: comparison of distinct pointer types lacks a cast
config.c:1511: error: ‘i’ undeclared (first use in this function)
config.c:1511: warning: comparison between pointer and integer
config.c:1511: error: lvalue required as increment operand
config.c:1512: error: array subscript is not an integer
config.c:1512: warning: initialization from incompatible pointer type
config.c:1525: warning: comparison between pointer and integer
config.c: In function ‘wpa_config_get’:
config.c:1551: error: ‘size_t’ undeclared (first use in this function)
config.c:1551: warning: statement with no effect
config.c:1551: error: expected ‘;’ before ‘i’
config.c:1553: warning: comparison of distinct pointer types lacks a cast
config.c:1553: warning: comparison of distinct pointer types lacks a cast
config.c:1554: warning: return from incompatible pointer type
config.c:1556: error: ‘i’ undeclared (first use in this function)
config.c:1556: warning: comparison between pointer and integer
config.c:1556: error: lvalue required as increment operand
config.c:1557: error: array subscript is not an integer
config.c:1557: warning: initialization from incompatible pointer type
config.c:1562: warning: return from incompatible pointer type
config.c: In function ‘wpa_config_get_no_key’:
config.c:1584: error: ‘size_t’ undeclared (first use in this function)
config.c:1584: warning: statement with no effect
config.c:1584: error: expected ‘;’ before ‘i’
config.c:1586: warning: comparison of distinct pointer types lacks a cast
config.c:1586: warning: comparison of distinct pointer types lacks a cast
config.c:1587: warning: return from incompatible pointer type
config.c:1589: error: ‘i’ undeclared (first use in this function)
config.c:1589: warning: comparison between pointer and integer
config.c:1589: error: lvalue required as increment operand
config.c:1590: error: array subscript is not an integer
config.c:1590: warning: initialization from incompatible pointer type
config.c:1599: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c:1603: warning: return from incompatible pointer type
config.c:1609: warning: return from incompatible pointer type
config.c: In function ‘wpa_config_update_psk’:
config.c:1622: error: ‘struct wpa_ssid’ has no member named ‘passphrase’
config.c:1623: error: ‘struct wpa_ssid’ has no member named ‘ssid’
config.c:1623: error: ‘struct wpa_ssid’ has no member named ‘ssid_len’
config.c:1624: error: ‘struct wpa_ssid’ has no member named ‘psk’
config.c:1624: warning: passing argument 1 of ‘pbkdf2_sha1’ from incompatible pointer type
config.c:1624: warning: passing argument 3 of ‘pbkdf2_sha1’ makes integer from pointer without a cast
config.c:1624: error: too many arguments to function ‘pbkdf2_sha1’
config.c:1626: error: ‘struct wpa_ssid’ has no member named ‘psk’
config.c:1627: error: ‘struct wpa_ssid’ has no member named ‘psk_set’
config.c:1627: warning: statement with no effect
config.c: In function ‘wpa_config_get_blob’:
config.c:1645: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1645: warning: assignment from incompatible pointer type
config.c:1647: warning: return from incompatible pointer type
config.c: In function ‘wpa_config_set_blob’:
config.c:1663: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1663: warning: statement with no effect
config.c: In function ‘wpa_config_free_blob’:
config.c:1676: error: ‘struct wpa_config_blob’ has no member named ‘data’
config.c: In function ‘wpa_config_remove_blob’:
config.c:1690: warning: initialization from incompatible pointer type
config.c:1695: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1695: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1695: warning: statement with no effect
config.c:1697: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1697: warning: assignment from incompatible pointer type
config.c:1702: error: ‘struct wpa_config_blob’ has no member named ‘next’
config.c:1702: warning: assignment from incompatible pointer type
config.c: In function ‘wpa_config_alloc_empty’:
config.c:1721: warning: assignment makes pointer from integer without a cast
config.c:1722: warning: comparison of distinct pointer types lacks a cast
config.c:1723: warning: return from incompatible pointer type
config.c:1729: warning: incompatible implicit declaration of built-in function ‘strdup’
config.c: In function ‘wpa_config_debug_dump_networks’:
config.c:1754: warning: implicit declaration of function ‘wpa_ssid_txt’
config.c:1754: error: ‘struct wpa_ssid’ has no member named ‘ssid’
config.c:1754: error: ‘struct wpa_ssid’ has no member named ‘ssid_len’
config.c:1754: warning: format ‘%s’ expects type ‘char *’, but argument 4 has type ‘int’
make: *** [config.o] Error 1

```

---

