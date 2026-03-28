# AmiTCP Patches for VBCC

This repository contains patches to make [AmiTCP](https://github.com/mheeres/AmiTCP) compile with the VBCC compiler and run optimally on Amiga systems.

## Patches

- **`AmiTCP-VBCC-full.patch`** - Modifies the AmiTCP source to compile using the VBCC compiler.
- **`AmiTCP-optimisations.patch`** - Optimisations to the core source code for improved performance on 68k Amiga architectures.

## Usage

### Prerequisites

You will need the following archive files and patch files in the same working directory:

- `AmiTCP-src-30b2.lha`
- `AmiTCP-api-30b2.lha`
- `AmiTCP-VBCC-full.patch`
- `AmiTCP-optimisations.patch`

### Steps

```sh
# 1. Extract the sources
lha x AmiTCP-src-30b2.lha
mkdir temp_api
cd temp_api
lha x ../AmiTCP-api-30b2.lha
mv AmiTCP-3.0b2/netinclude ../AmiTCP-3.0b2/src/
cd ..
rm -rf temp_api

# 2. Enter the source directory
cd AmiTCP-3.0b2

# 3. Apply the patches
patch -p1 < ../AmiTCP-VBCC-full.patch
patch -p1 < ../AmiTCP-optimisations.patch

# 4. Build
cd src
bash build_vbcc.sh
```

Ensure your VBCC include paths and environment variables are configured correctly before building.
