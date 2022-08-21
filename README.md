# Optiplex 7070

# Details

| OpenCore Version | 0.8.3 |
| --- | --- |
| macOS Version | 12.5.1 (Big Sur) |
| SMSBios | iMac19,1 |

# Hardware Specifications

| Hardware | Specification | Status |
| --- | --- | --- |
| CPU | Intel Core i7-9700 | ✅ Working |
| GPU | Intel UDH Graphics 630 | ✅ Working |
| Chipset | Intel Q370 | ✅ Working |
| RAM | DDR4 16GB x2 | ✅ Working |
| Audio | Realtek ALC3234 | ✅ Working |
| WiFi | Broadcom BCM94360NG  | ✅ Working |
| Bluetooth | - | ✅ Working |
| LAN | Intel i219-LM | ✅ Working |
| SSD | WD SN550 | ✅ Working |

# Using EFI

> It is suggested that a different SMSBios is used instead. Please also ensure that you have [setup your bootable drive](https://dortania.github.io/OpenCore-Install-Guide/installer-guide/)
> 

Follow these instructions to change SMSBios:

1. Download [ProperTree](https://github.com/corpnewt/ProperTree/archive/refs/heads/master.zip) and [GenSMSBIOS](https://github.com/corpnewt/GenSMBIOS/archive/refs/heads/master.zip)
2. Open the `config.plist` with ProperTree and use GenSMSBIOS to generate a the SMSBIOS data 
    - Pick option 1 for downloading MacSerial and option 3 and enter `iMac19,1`.
        
        You should get an output similar to the following:
        
        ```bash
        Type:         iMac19,1
        Serial:       CXXXXXXXXXXX
        Board Serial: CXXXXXXXXXXXXXXXX
        SmUUID:       XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
        ```
        
    - In the `config.plist`, map the above output to the following values
        
        The `Type` part gets copied to Generic → SystemProductName.
        
        The `Serial` part gets copied to Generic → SystemSerialNumber.
        
        The `Board Serial` part gets copied to Generic → MLB.
        
        The `SmUUID` part gets copied to Generic → SystemUUID.
        
    - Save the file
3. Boot with the necessary [BIOS settings](#BIOS-Settings)

# BIOS Settings

| SATA Operation | ACHI |
| --- | --- |
| Enable Mediacard | Enabled |
| Fast Boot | Thorough |
| Secure Boot | Disabled |
| TMP 2.0 Security | Disabled* |
| Intel SGX | Disabled |
| VT for Direct I/O | Disabled |

*- Enabled for me and machine functions properly