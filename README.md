# Keystone vNode

A live stats page for **Keystone vNode**, a validator on the [Vitreus](https://vitreus.io) network. If you're thinking about staking (cooperating) with Keystone, this page shows how the node is doing right now, read straight from the chain.

**Live page:** https://YOUR-GITHUB-USERNAME.github.io/keystone-vnode/

**Validator address:** `0x4a5aE431Fa51c67096Bf5763A6b8C00fA44d8edA`

Always check that the address you stake to ends in **…8edA**. This repo and the live page are the only places it's published by the operator.

## What it shows

- **Status:** whether Keystone is in the active validator set this session
- **Commission** and how it compares with the network minimum
- **Reputation tier** and rank among all validators, plus the stake bonus that tier earns
- **Blocks produced** this hour against the network median
- **Cooperators:** how many there are and how many paid slots (of 128) are still open
- **Total stake:** the operator's own stake and stake from cooperators, with a 14-day chart
- **Track record:** whether any stake has ever been slashed
- **Before you stake:** unbonding time, payout rules and slashing risk, read from the chain's own settings

Every number is fetched live each time the page opens and refreshes every 2 minutes. Nothing is typed in by hand, so the page can't overstate anything.

## It's read-only and safe to open

This page **can't touch your funds**. It:

- **only reads public chain data.** It never asks for a wallet, a recovery phrase, a private key or a signature, and contains no code that could send a transaction.
- **has no backend, tracking or analytics.** It stores nothing about you and sends nothing anywhere.
- **makes only these connections:**
  - `wss://rpc-mainnet.vtrs.io`: the public Vitreus RPC, to read chain data
  - `esm.sh/@polkadot/api@16.5.6`: the standard Polkadot JavaScript library, pinned to an exact version so it can't change underneath you
  - `fonts.googleapis.com`: the page fonts

**Don't take my word for it.** The whole page is one readable file, [`index.html`](index.html). Search it for `signAndSend`, `tx.` or `web3Enable`: none of them appear. Any page that asks you to *sign* something in order to "view stats" is not this one.

## Run it yourself

You don't need to trust the hosted copy:

1. Download `index.html` (**Code → Download ZIP**, or the download button on the file).
2. Double-click it. It opens in your browser and connects straight to the Vitreus chain.

This works on a computer. On a phone, use the live link instead: phones open downloaded HTML files in a preview that doesn't run scripts.

## Check the numbers independently

- **Explorer:** https://explorer.vtrs.io/address/0x4a5aE431Fa51c67096Bf5763A6b8C00fA44d8edA
- **vScan operators:** https://vscango.com/operators
- **Raw chain state:** [polkadot.js apps](https://polkadot.js.org/apps/?rpc=wss://rpc-mainnet.vtrs.io:443#/chainstate). Use `energyGeneration.validators`, `energyGeneration.erasStakers` and `reputation.accountReputation` with the address above.

## How to stake

1. Copy the validator address above.
2. In **vApp**, go to staking and choose a vNode to cooperate with.
3. Paste the address and confirm it ends in **…8edA**.
4. Enter an amount, review and sign **in vApp**.

Your stake starts counting once the next validator selection takes effect, usually within an era or two (eras are 4 hours). Unstaking takes 42 eras, about 7 days.

## Disclaimer

This is an independent operator page. It isn't affiliated with or endorsed by Vitreus. Nothing here is financial advice. Staking has risks, including slashing and changes to network rules. Do your own research and verify everything on-chain.

The reputation-bonus figures follow the formulas in Vitreus's open-source node code ([power-plant](https://github.com/Vitreus-Foundation/power-plant)) and may change if the network is upgraded.

## License

MIT. Use and adapt freely; please change the address to your own if you fork it.
