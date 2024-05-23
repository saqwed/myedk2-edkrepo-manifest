# edkrepo

Create a edkrepo manifest for myedk2.

## How to use it?

Install edkrepo first.

- Python3.8 or above
  - Download and install [python-3.12.3-amd64.exe](https://www.python.org/ftp/python/3.12.3/python-3.12.3-amd64.exe)
- Download [EdkRepoSetup-3.2.2.0.exe](https://github.com/tianocore/edk2-edkrepo/releases/download/edkrepo-v3.2.2/EdkRepoSetup-3.2.2.0.exe)
  - Install package setuptools by `pip install setuptools` first.
  - Install EdkRepoSetup-3.2.2.0.exe.

## Usage

```batch
REM Run below command to see how many manifest repos maintained by edkrepo
edkrepo manifest-repos list

REM Add myedk2 manifest repo
edkrepo manifest-repos add myedk2 https://github.com/saqwed/myedk2-edkrepo-manifest main myedk2

REM Remove myedk2 manifest repo
REM edkrepo manifest-repos remove myedk2

REM After add/remove manifest repos, update manifest database to get the latest manifests,
REM the database created at c:\ProgramData\edkrepo\edkrepo_user.cfg and clone to c:\ProgramData\edkrepo\myedk2\
edkrepo update-manifest-repo

REM List edkrepo maintained repos
edkrepo list-repos

REM Clone project myedk2 and the default combination master to folder myedk2
edkrepo clone myedk2-master myedk2

REM Clone project myedk2 and the default combination edk2-stable202402 to folder myedk2_tag202402
REM Use parameter --single-branch to clone only the specific branch.
edkrepo clone --single-branch myedk2-tag202402 myedk2 edk2-stable202402
```

## issue?

When run `edkrepo clone` may see below error and breaking clone process.

```batch
error: RPC failed; curl 92 HTTP/2 stream 5 was not closed cleanly: CANCEL (err 8)
error: 1980 bytes of body are still expected
fetch-pack: unexpected disconnect while reading sideband packet
fatal: early EOF
fatal: fetch-pack: invalid index-pack output
```

Run `git config --global http.postBuffer 4096M` and try again

Refer to: [error: RPC failed; curl 92 HTTP/2 stream 5 was not closed cleanly before end of the underlying stream](https://github.com/orgs/Homebrew/discussions/4069)
