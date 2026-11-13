# Dead Lie Still
A wargame where defeat isn't the end.

This wargame was inspired by [Trolligarch's video](https://www.youtube.com/watch?v=MMjpej5Bcpo).

## General
The map is a 13-diameter hexagonal grid. Before the game starts, players choose starting locations without seeing the choices of others. Multiple players can occupy a tile. When the game starts, all players' locations are revealed and publicly visible for the rest of the game.

Players start with 1 blue token \(B\), 1 red token \(R\), and 3 lives \(L\). Players spend tokens on trading, moving, and attacking. Players also produce tokens.

Players who lose all of their lives become rogues, losing all blue token but keeping red token. Rogues no longer appear on the map, but can interact with players by trading and spying. Rogues can only poduce red tokens.

Players that eliminate other players gain all blue token of the eliminated player. Only the player that lands the killing blow gains the blue tile.

The game takes place over a series of rounds lasting exactly 1 day. Players and rogues can select their actions at any time over the course of a round. At the end of a round (EoR), which occurs at a daily fixed time, all actions are simultaneously performed at a fixed order.

The last player alive is declared the winner. The remaining players gain points for the number of rounds survived. Rogues gain additional points for each blue token (B) they own at the end of the game.


## Actions

Players can choose any combination of the following actions (including multiple of the same action). Target refers to another player or rogue that is not youself. Note that all actions targeting players are limited by a 7-diameter range around the acting player. Players can interact with any rogue.

| Action | Target | Cost | Effect |
| --- | --- | --- | --- |
| Attack | Player | 1 R | Target -1 L |
| Move | None | 1 R | You move to a tile of choice |
| Trade \(R\) | Player or Rogue | 1 R | Target +1 R |
| Trade \(B\) | Player or Rogue | 1 B | Target +1 B |
| Rebuild | None | 3 B | You +1 L* |

Players also choose between producing a red and blue token.

*Players' life counts are maxed at 5 at the end of a round. This does not mean it is useless to rebuild when you are at 5 lives, see [Order](#Order).

---

Rogues can choose any combination of the following actions (including multiple of the same action). Rogues are not subject to range limits, and can interact with any player or rogue.

| Action | Target | Cost | Effect |
| --- | --- | --- | --- |
| Trade \(R\) | Player or Rogue | 1 R | Target +1 R |
| Trade \(B\) | Player or Rogue | 1 B | Target +1 B |

Rogues also have the choice between producing a red token or spying on a player. Spying on a player provides the rogue info on the player's red token, blue token, and life counts.

---

Trade and attack actions can be selected as either regular or priority. See [Order](#Order) for how that influences gameplay.

## Order

All actions and events in the game occur at the end of a round. This is the order in which they occur:

* Token Generation
* Trade (Priority)
* Attack (Priority)
* Move
* Trade (Regular)
* Attack (Regular)
* Rebuild
* Players with &le; 0 lives become rogues
* Blue tokens distributed to last attackers
* Players with > 5 lives are set to 5 lives
* Spy information is given

### Tiebreakers

Trading and attacking actions can occur at the same time, so tiebreakers are employed to determine order:

Attacking: Given an action A attacks B, the tiebreakers are considered in the following order, where the qualifying action moves first:
* A can afford the action
* B has the least lives
* A has the most number of attacking actions targeted towards B
* A has the most number of attacking actions
* A has the most red tokens
* Random chance

Trading: Given an action A trades B, the tiebreakers are considered in the following order, where the qualifying action moves first:
* A can afford the action
* A has the most number of the token being traded
* B has the least number of the token being traded
* Random chance

Note that tiebreakers are employed before actions are processed. This means that tiebreaking conditions (e.g. # of red tokens, # of attack actions) are taken from the very beginning of EoR, before any action occurs. This also means that actions are not currently affordable are still considered for tiebreakers.

### Clarifications

* Attack and trade only work if the target is within range of the acting player at that moment.
* If an attack is out of range, the red tokens are still spent but no damage is dealt.
* An attack that takes the target's lives to a negative value is not refunded.
* If a trade is out of range, tokens are refunded.
* If an action's acting player does not have the token count to perform said action at that moment, that action is cancelled and the tokens are refunded.
* If a player who becomes a rogue is spied on, the acting rogue gets the information of who the last attacker was.
* Lives can go negative and go above 5 while the actions are applied. Tokens cannot go negative at any time.
* The last attacker of a dead player is the acting player of the attack that brings the target down to 0 lives including lives gained through rebuild. For example:
    * X: 2 lives. Order: A attacks X, B attacks X, C attacks X, D attacks X, X rebuilds.
    * X becomes a rogue. X had 3 lives in total \(including rebuild\), so C is the last attacker.