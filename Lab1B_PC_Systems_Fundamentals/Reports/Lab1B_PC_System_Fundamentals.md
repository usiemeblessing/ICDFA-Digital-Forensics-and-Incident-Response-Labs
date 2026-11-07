# Lab 1B: PC System Fundamentals, Disk Sectors and Partition Analysis

**Course:** CIP-B101, Basic Computer Skills for Digital Forensics  
**Author:** Usieme Blessing Onome  
**Platform:** Windows 10 Home (Kali Linux used for one calculation check)

## Overview

I examined my own laptop the way a forensic investigator would: identifying the system, mapping its disk layout, and calculating partition sizes from raw sector counts. Everything was done with read-only commands, and nothing on the disk was changed.

## What I Did

- Identified the system, storage and boot mode
- Looked at running processes and explained programs, processes and threads
- Calculated disk and partition sizes from sectors
- Inspected the partition table with three different tools
- Explained how a PC boots and how MBR and GPT differ
- Identified the file systems in use

## Tools Used

`msinfo32` | `systeminfo` | `wmic` | `tasklist` | Disk Management | PowerShell | DiskPart | Kali Linux terminal

## Key Findings

| Item | Result |
| --- | --- |
| Device | HP Spectre x360, Windows 10 Home |
| Processor / RAM | Intel Core i7-7500U / 16 GB |
| Disk | Samsung 512 GB (about 477 GB as computers count it) |
| Partition style | GPT, 5 partitions, 512-byte sectors |
| Boot mode | UEFI, Secure Boot on |
| File system | NTFS on all volumes I could identify |

## Sector Calculation

Size = number of sectors x bytes per sector.

| Partition | Start sector | End sector | Sectors | Size |
| --- | --- | --- | --- | --- |
| 1 (EFI System) | 2,048 | 534,527 | 532,480 | 0.2539 GB (260 MB) |
| 2 (Reserved) | 534,528 | 567,295 | 32,768 | 0.0156 GB (16 MB) |

My calculated sizes matched what Windows reports. I also verified all five partitions with a PowerShell command, and the results agreed.

## What I Learned

- Evidence sits in several layers (user, application, operating system, disk, memory), and the same action can leave traces in more than one.
- Different tools report slightly different sizes because of units (1024 vs 1000) and rounding, not because of errors.
- GPT disks keep a backup of their partition data, which can help an investigator validate or recover partition information.
- Investigators should use read-only methods and record the system, disk layout and file systems accurately so findings can be trusted.

## Skills Demonstrated

System identification | Disk and partition analysis | Sector and size calculation | Boot process and partition scheme knowledge | File system identification | Read-only evidence handling | Technical report writing

## Notes

Personal details such as the computer name, username and serial number were not exposed in the screenshots.
